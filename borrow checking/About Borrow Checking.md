> 📚 **Borrow checking** is a *compile-time* static tool that guarantees runtime ownership. It is Rust's way of avoiding data ownership misuse without the need for a runtime garbage collector, and significantly reduces mutability errors by restraining the scope of access to a variable (in particular in a multithreaded context).

---
## Rules

**🚧 TODO 🚧**

---
## Flow Model

> 💡*This is a high-level mental model designed to simplify and make more intuitive the notion of ownership in Rust.*

> 📚 We define a **flow** as a set of connections or imaginary *lines* between variable initialization, mutations and use.

- A **flow** *starts* at variable initialization.
- A **flow** *ends* when a variable goes out of scope. New lines cannot be added to the flow after that.
- A **flow** is *frozen* when it's variable is borrowed. It may resume once the borrow has gone out of scope.
- *Mutating* a variable marks a new point in a **flow**, creating a dependency relation between this and the variable's previous state.
- Two **flows** cannot have conflicting access over a same variable, and a mutable  flow cannot exist at the same time as an immutable flow.

*ex:*
```rust
// let's trace this variable's flow
// x is uninitialized so far, so the flow doesn't start here
let mut x;

x = 20;             // x' 1.     (the flow of x)
                    // |
let y = &x;         // x' 2.   y' (the flow of y)
                    // ║       |
x = 43;             // x' 3.   |
                    //         |
assert_eq!(*y, 20); //         y'
```

The above code is invalid. Let's break it down:

1. The flow of `x` is created.
2. `x` is borrowed, freezing it's flow.
3. Attempted mutation of  `x` while it's flow is frozen. This breaks ownership rules.

To make this code valid, we can do the following:

```rust
let mut x;

x = 20;                // x'      1.
                       // |
{                      // |
	let y = &x;        // x'  y'  2.
                       // ║   |
	assert_eq!(*y, 20) // ║   y'
	                   // ║   |
}                      // x'  y'  3.
                       // |
x = 43;                // x'
```

1. The flow of `x` is created.
2. `x` is borrowed, freezing it's flow. The flow of `y` begins.
3. `y` goes out of scope, ending it's flow and unfreezing the flow of `x` (borrow has ended).
4. `x` is reassigned once it's flow is no longer frozen.

> ℹ️ *Note that if a new variable is created with the same name as a previous variable, it does not inherit or replace that variable's flow, but starts its own. This is referred to as* **shadowing**.

---
## Low-level model

**🚧 TODO 🚧**