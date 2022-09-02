[[Rust]] is a [[statically typed]] language. The compiler typically does a good job at inferring types where applicable, however the source of any ambiguity must be corrected before the program will compile.

## Scalar types

A [[scalar type]] represents a single value. Rust has 4: [[integers]], [[floating-point numbers]], [[Booleans]], and [[characters]].

### Integers

Integers in [[Rust]] are either signed or unsigned. 

Length | Signed | Unsigned
------- | ------ | -------
8-bit | i8 | u8
16-bit | i16 | u16
32-bit | i32 | u32
64-bit | i64 | u64
128-bit | i128 | u128
arch | isize | usize

Signed integers are represented in [[two's complement]] representation.

`isize` and `usize` types depend on the architecture of the computer (ie. 64 bits on 64-bit architecture, 32 bits on 32-bit architectures).

Integer literals can be used in [[Rust]] as a means of representing static numeric values;

`41444, 0xff, 0o33, 0b1100, b'T' (Byte, only u8 is allowed)`

They can use `_` character as a visual separator to make numbers easier to read.

`98_222, 0b1111_0011`

### Floating points

[[Rust]] uses `f32` and `f64` for [[floating-point numbers]]. 

Floating-point numbers are `f64` by default, and only `f32` when specified. This is because `f64` is just as fast as `f32` on modern CPUs but carry increased precision.

### Numeric operations

[[Rust]] supports addition, subtraction,  multiplication, division, and remainder. 

Integer division rounds down.

```rust
fn main() { 
	// addition 
	let sum = 5 + 10; 
	// subtraction 
	let difference = 95.5 - 4.3; 
	// multiplication 
	let product = 4 * 30; 
	// division 
	let quotient = 56.7 / 32.2; 
	let floored = 2 / 3; // Results in 0 
	// remainder 
	let remainder = 43 % 5; }
```

### Booleans

The [[Boolean]] type in [[Rust]] has two possible values: `true` and `false`. Booleans are one byte in size.

```rust
let f: bool = false;
```

### Characters

[[Rust]]'s [[character]] type is its most primitive alphabetic type. 

```rust
let c = 'z';
let z: char = 'Z';
let some_emoji = '😻'
```

Characters are four bytes in size and represents a [[Unicode Scalar Value]]. This means it can encode pretty much anything (including emojis).

## Compound types

A compound type groups multiple values into one type.

### Tuples

The [[tuple]] type in [[Rust]] is a way of grouping together values.

```rust
let tup: (i32, f32, u16) = (1000, 4.1, 4);
```

Tuples can be destructured using pattern matching:

```rust
let (x, y z) = tup;
```

You can also access individual elements by using `.` followed by the index:

```rust
let x = tup.0;
let y = tup.1;
let z = tup.2;
```

### Arrays

[[Rust]] requires each element of an [[array]] to have the same type, and for the [[array]] to have a fixed length.

```rust
let a = [1, 2, 3, 4, 5];
```

**Arrays are allocated on the stack rather than the heap.**

Array's type and length can be annotated:

```rust
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

Arrays can be shorthand initialized to all contain the same element:

```rust
let a = [3; 5]; // [3, 3, 3, 3, 3]
```

Array elements are accessed as usual.

```rust
let a = [1, 2, 3, 4, 5];
let first = a[0];
```

Accessing an element outside of an array's bounds will produce a panic, resulting in a runtime error.
