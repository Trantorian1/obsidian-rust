> 📚 **Ownership** in Rust is a principle by which variables take sovereignty over the right of access to their data. A variable cannot have multiple owners, and ownership only persists as long as that variable's scope.

Ownership is defined though assignment. This does not matter for basic types which can be copied, however this is less evident for non-native types, such as structures. When a variable is assigned a value from another variable which cannot be copied, it takes ownership of that variable, meaning the previous variable can no longer access the value of the data it is pointing to. Ownership is then set once more upon subsequent assignments.

> ℹ️ Assignment of a data is giving up ownership.

*ex*:
```rust
// you can see the act of passing a value to 'foo'
// as an assignment to vec, thus loosing ownership
fn foo(vec: Vec<i32>) -> Vec<i32> {
	// code...

	// returning vec, ownership is restored
	vec
}

fn main() {
	let vec = vec![1, 2, 3];
	foo(vec);

	// vec has been borrowed and not restored,
	// this code will not compile
	println!("{:?}", vec);
}
```

*vs*:
```rust
// you can see the act of passing a value to 'foo'
// as an assignment to vec, thus loosing ownership
fn foo(vec: Vec<i32>) -> Vec<u32> {
	// code...

	// returning vec, ownership is restored
	vec
}

fn main() {
	let mut vec = vec![1, 2, 3];
	// restores ownership of vec
	vec = foo(vec);

	// this no longuer causes a compilation error
	println!("{:?}", vec);
}
```

## References

> 📚 **References** allow to pass a value without taking ownership from it. They can be mutable or immutable.

A reference can be seen as 'view' onto a variable, allowing to access it while the owner of the variable has not been cleaned up.

Note that a reference **cannot outlive the owner of the variable**. When the owner goes out of scope, all references will be invalidated.

```rust
// foo does not take ownership of 'vec'
// since it now uses a reference
fn foo(vec: &Vec<i32>) {
	// code...
}

fn main() {
	let vec = vec![1, 2, 3, 4];
	// uses a reference to vec instead
	// of loosing ownership
	foo(&vec);

	// this will no longuer cause issues
	// as vec still has ownership
	println!("{vec:?}");
}
```

---
*related:* [[Lifetime]]