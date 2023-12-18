> 📚 **Structures** in Rust can be seen as **classes without inheritance**: they implement all the functionality and modularity of classes as seen in languages such as C++ while maintaining a flat inheritance structure. This allows for easy modelling of complex data.

> 💡Consider exploring alternatives to inheritance such as **Entity Component Systems** (or ECS).

---

## Structure Types
*There are three types of structures in Rust*

- 'classic' struct, similar to C structs
	They can be used to store data in ways that are easy to access and manipulate.
  
- tuple structs
	They are useful to represent data for whom name access is not relevant.
  
- unit structs
	They can be used as markers for traits or state in a type-safe way.

*syntax:*
```rust
// classic struct
struct Point {
	x: f32,
	y: f32,
}

// tupple struct
struct Pair(i32, i32);

// unit structs 
struct Unit;
```

---

## Destructuring

> 📚 **Destructuring** allows for easy access to structure member data using *pattern matching*.

*syntax:*
```rust
match structure {
	Structure { x, y } => {
		// code
	}
```

*ex:*
```rust
struct Point {
	x: f32,
	y: f32,
}

let position = Point { 12.3, 14.6 };

match position {
	Point { x, y } => println!("current position is [{}, {}]", x, y);
}
```

Destructuring can also be use to **only extract certain fields** from a structure.

*syntax:*
```rust
match structure {
	Structure { x, ... } => {
		// code
	}
}
```

*ex:*
```rust
struct Point {
	x: f32,
	y: f32,
}

let position = Point { 12.3, 14.6 };

match position {
	// note that we only destructured 'y', 
	// so we have no way of accessing 'x' !
	Point { y, ... } => println!("current position is [..., {}]", y);
}
```

---

## Member Functions

> ℹ️ **Member Functions** in Rust work the same way as class member functions in OOP languages such as C++, though their syntax for declaration is somewhat different.

*syntax:*
```rust
struct Point {
	x: f32,
	y: f32,
}

impl Point {
	// functions that do not take 'self'
	// as first parameter are static
	pub fn distance(a: Point, b: Point) -> Self {
		Self { x: a.x - b.x, y: a.y - b.y }
	}

	// `self` refers to the instance
	// this function is being called on
	pub fn distance_to(&self, other: Point) -> f32 {
	    let width = self.x - other.x;
        let height = self.y - other.y;

        (width * width + height * height).sqrt()
    }

	// for functions that mutate the calling object,
	// 'self' must be specified as mutable
    pub fn translate_mut(&mut self, other: Point) {
        self.x += other.x;
        self.y += other.y;
    }
}
```

---

## Constructors

> ℹ️ While constructors are not natively supported in Rust, similar functionality can be achieved using **member functions**.

By convention, you should name your constructors `new`.

*ex:*
```rust
pub struct Point {
	x: f32,
	y: f32,
}

impl Point {
	// 'Self' refers to the type being implemented
	pub fn new(x: f32, y: f32) -> Self {
		Self { x: x, y: y }
	}
}
```

---
*related:* [[Enums]], [[rust/code structure/Functions|Functions]], [[Pattern Matching]]