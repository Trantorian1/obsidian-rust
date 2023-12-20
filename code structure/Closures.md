> 📚 **Closures** are a concept related to functional programming. They are equivalent to **lambdas** in other languages, that is to say assignable functions.

> ⚠️ Note that Rust does not have very good support for closure / function types. More on that down below.

*syntax:*
```rust
let closure1 = |arg1: type, arg2: type| {
	arg1 + arg2
};

// you can also define simple closures in a single line
let closure2 = |arg1: type, arg2: type| arg1 + arg2;
```

Closures capture their scope, making them especially useful for allowing data mutation in function without exposing the original variable but instead handing the logic of mutation. This pattern is especially useful in GUI libraries, such as [Jetpack Compose](https://developer.android.com/jetpack/compose).

*ex:*
```rust
fn main() {
	// note that capturing a variable inside
	// a closure is equivalent to borrowing it
	let mut x = 42;
	let mult = |scale: i32| x * scale;

	// 'x' is captured by 'mult' so that it's value can
	// still be accessed from within the scope of the closure
	println!("x * 10 = {}", mult(10))
}
```

---
## Closure Traits

> ℹ️ Closure in Rust all implement the `Fn` trait, with some variations possible under the form of `FnMut` and `FnOnce`

### `Fn`

> 📚 `Fn` marks simple functions and closures which do not mutate any parameters or captured variables.

### `FnMut`

> 📚 `FnMut`, as the name implies, marks functions and closures which mutate their parameters or captured variables.

*ex:*
```rust
fn main() {
	let mut x = 0;
	let mut add = |y: i32| x += y;

	add(42);
	println!("x: {x}");
}
```

### `FnOnce`

> 📚 `FnOnce` marks functions and closures which can only be called once. Any subsequent attempt to call the function will throw an exception.

To mark a closure as `FnOnce`, you must call the `move` operator on the closure.

> ℹ️ `move` make a closure take ownership of the variables it captures instead of using them by reference.

```rust
fn main() {
	let name = String::from("Trantorian");
	let once = move || name;

	// 'name' can no longer be accessed after
	// this as 'once' has taken ownership of it

	println!("{}", once())

	// 'once' can no longuer be called
}
```