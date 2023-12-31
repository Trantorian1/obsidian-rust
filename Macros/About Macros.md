**Macros** are an extremely powerful meta-programming tool in rust which allow for both cleaner code as well as compile-time pre-computation. Unlike programming most programming languages like C or C++, Rust macros offer more than just text replacement and have a rich type system which essentially allow them to access the full Rust **AST**[^1] during compilation. This leads to extreme flexibility, up to implementing new language features or full **DSL**s [^2] **with no performance overhead as compared to standard rust**.

---

## Structure

- [[Macro Syntax]]
- [[Declarative Macros]]

---
*related:* [The Little Book of Rust Macros](https://veykril.github.io/tlborm/decl-macros/macros2.html)

[^1]: An **A**.**S**.**T**, or **A**bstract **S**yntax **T**ree, is a collection of tokens representing the various elements of a grammar, here the Rust language. Essentially, the Rust AST is an hierarchical collection of describing the structure of a source file.

[^2]: A **D**.**S**.**L**, or **D**omain **S**pecific **L**anguage, is a programming language made to be applied to a narrow set of problems. It is highly specified in one or a small set of tasks and is therefore particularity well suited at that task, at the cost of generality. Examples of DSLs are: JSON, Markdown, SQL...