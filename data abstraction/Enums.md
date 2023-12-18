> 📚 **Enums** in Rust allow for the structured representation of **different variations of related data**.

> 📚 **Variations** is the name given to different enum instance.

Rust Enums are more powerful than in languages such as C and C++, as the can hold additional data related to each *variation*. For example, one *variation* might contain a string error message while the other might contain JSON information.

*syntax:*
```rust
enum EnumName {
	Variation1,
	Variation2
}
```

*ex:*
```rust
enum IPKind {
	IPV4(u8, u8, u8, u8),
	IPV6(u32, u32, u32, u32)
}
```

Enum *variations* in rust can hold the following data:
- none,
- structure,
- tuple

*ex:*
```rust
enum EnumName {
	DataNone,
	DataStruct { x: f32, y: f32 },
	DataTuple(u32, u32)
}

let x = EnumName::DataNone;
let y = EnumName::DataStruct { x: 0f32, y: 0f32 };
let z = EnumName::DataTuple(0, 0);
```