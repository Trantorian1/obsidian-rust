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

---
*related:* [[Enums]], [[rust/code structure/Functions|Functions]], [[rust/control flow/Conditions|Conditions]]