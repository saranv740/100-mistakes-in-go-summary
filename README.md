# 100-mistakes-in-go-summary

## 1. Code and project organization
1. Avoiding shadowed variables can help prevent mistakes like referencing the wrong variable or confusing readers.
2. Avoiding nested levels and keeping the happy path aligned on the left makes building a mental code model easier.
3. When initializing variables, remember that init functions have limited error handling and make state handling and testing more complex. In most cases, initializations should be handled as specific functions.
4. Forcing the use of getters and setters isn’t idiomatic in Go. Being pragmatic and finding the right balance between efficiency and blindly following certain idioms should be the way to go.
5. Abstractions should be discovered, not created. To prevent unnecessary complexity, create an interface when you need it and not when you foresee needing it, or if you can at least prove the abstraction to be a valid one.
6. Keeping interfaces on the client side avoids unnecessary abstractions.
7. To prevent being restricted in terms of flexibility, a function shouldn’t return interfaces but concrete implementations in most cases. Conversely, a function should accept interfaces whenever possible.
8. Only use ```any``` if you need to accept or return any possible type, such as ```json.Marshal```. Otherwise, any doesn’t provide meaningful information and can lead to compile-time issues by allowing a caller to call methods with any data type.
9. Relying on generics and type parameters can prevent writing boilerplate code to factor out elements or behaviors. However, do not use type parameters prematurely, but only when you see a concrete need for them. Otherwise, they introduce unnecessary abstractions and complexity.
10. Using type embedding can also help avoid boilerplate code; however, ensure that doing so doesn’t lead to visibility issues where some fields should have remained hidden.
11. To handle options conveniently and in an API-friendly manner, use the functional options pattern.
12. Following a layout such as project-layout can be a good way to start structuring Go projects, especially if you are looking for existing conventions to standardize a new project.
13. Naming is a critical piece of application design. Creating packages such as ```common```, ```util```, and ```shared``` doesn’t bring much value for the reader. Refactor such packages into meaningful and specific package names.
14. To avoid naming collisions between variables and packages, leading to confusion or perhaps even bugs, use unique names for each one. If this isn’t feasible, use an import alias to change the qualifier to differentiate the package name from the variable name, or think of a better name.
15. To help clients and maintainers understand your code’s purpose, document exported elements.
16. To improve code quality and consistency, use linters and formatters.
