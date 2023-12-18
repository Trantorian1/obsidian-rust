> 📚 **Expressions** is any section of code that computes a value. This includes variable assignment (*not declaration*), arithmetic operations, function calls, control flow...

> 📚 **Declarations** do not hold a value.

*ex:*
```rust
let x = 2; // this is a declaration

x = 2; // this is an expression
```

The end of an expression is marked by a `;`.

ex:
```rust
let x = 12;

let y = if x < 10 {
	1
} else {
	2
}; // expression ends at the end of the `if` before 
   // being consumed by the  decleration of y

let z = if x < 10 {
	1; // expression ends here, will return `()` instead of 1
} else {
	2; // expression ends here, will return `()` instead of 2
};
```