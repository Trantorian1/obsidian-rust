> 📚 **Generics** in Rust function similarly to as in other languages such as C++ in the sens that they allow for polymorphism in code execution.

*syntax:*
```rust
<T: Trait>
```

*ex:*
```rust
trait Animal {
	fn make_sound(&self);
}

struct Cat;
struct Dog;

impl Animal for Cat {
	fn make_sound(&self) {
		println!("meow");
	}
}

impl Animal for Dog {
	fn make_sound(&self) {
		println!("wof");
	}
}

fn animal_greet<T: Animal>(animal: T) {
	animal.make_sound();
}

fn main() {
	let dog = Dog;
	let cat = Cat;

	animal_greet(dog);
	animal_greet(cat);
}
```

---

## `where`

> 📚 `where` in Rust allows you to specify the type of generic you want to accept.

*syntax:*
```rust
<T, V>...
where
	// any variable using T will need
	// to implement the `Clone` trait
	T: Clone,
	// it is also possible to force a
	// generic to implement multiple traits
	V: Clone + Add,
```

*ex:*
```rust
fn greater<T>(a: T, b: T) -> T
where
	T: PartialEq,
{
	if (a > b) {
		a
	} else {
		b
	}
}
```
