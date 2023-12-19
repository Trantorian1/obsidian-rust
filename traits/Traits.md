> 📚 **Traits** can be seen as Rust's version of **Interfaces** by contractually forcing the implementation of certain functions.

*syntax:*
```rust
trait MyTrait {
	fn foo() -> Baz;

	// Traits can also provide default implementations for functions.
	fn greet() {
		println!("Hello, World!");
	}
}
```

*ex:*
```rust
trait Identity {
	fn getName() -> String;
}

struct Person {
	name: String,
}

impl Identity for Person {
	fn getName() -> String {
		&self.name
	}
}
```

---

## Supertraits

> 📚 **Supertraits** are **traits** which implement other traits. They can be seen as Rust's version of **inheritance**.

*syntax:*
```rust
trait A {}

trait B: A {}
```

> ⚠️ Any structure implementing a child trait also need to implement the methods of it's **supertrait**. This can be used to force the implementation of related behavior for traits that might be interdependent.

*ex:*
```rust
trait Transformation {
	fn transform();
}

trait Translation: Transformation {
	fn translate();
}

struct SmoothTranslation {}

impl Translation for SmoothTranslation {
	// implements supertrait methods
	fn transform() {
		&self.translate();
	}

	// implements child trait methods
	fn translate() {
		// code...
	}
}
```

---

## Trait Derivation

> ℹ️ It is possible for the Rust compiler to provide default implementations of certain standard language traits. This is referred to as **trait derivation**.

*syntax:*
```rust
#[derive(Trait)]
struct MyStruct {}
```

*ex:*
```rust
#[derive(Clone, Debug, Eq)]
struct Point {
	x: f32,
	y: f32,
}

fn main() {
	let point1 = Point { x: 0.0, y: 0.0 };
	let point2 = point1.clone();
}
```

> ⚠️ Note that only certain default traits can be derived.

| Trait            | Implements                                       |
| ---------------- | ------------------------------------------------ |
| Clone            | `clone()`: deep copy                             |
| Copy             | `copy()`: shallow copy                           |
| Debug            | `fmt()`: debug string representation for display |
| PartialEq & Eq   | `eq()`: compares two objects                     |
| PartialOrd & Ord | `partial_cmp` & `cmp`: ordering objects          |

