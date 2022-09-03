# Ownership in Rust

Ownership is how [[Rust]] handles memory management. It is very strict at compile time and very fast at runtime, but has a larger learning curve than other methods.

## [[Rules of ownership in Rust]]

1. Each value in [[Rust]] has an *owner*
2. There can only be one owner at a time
3. When the owner goes out of scope, the value will be dropped

### Variable scope

The relationship between scopes and when variables are valid is similar to other programming languages. The only one that may be slightly different is the ***block scope***.

```rust
fn main() {
	let x = 0; // function scope
	{
		let y = x + 1; // block scope
	}
	println!("y is {y}"); // will error
}
```

## Heap data types

Ownership in [[Rust]] applies strictly to variables defined in the heap (see [[Stack and heap]]).

Types like `String` are stored in the heap because their size cannot be known at compile time. We need a way to both allocate this unknown length variable at runtime, and return the memory once we're done using it.

Allocation of memory is done similarly to other languages:

```rust
let s = String::from("hello");
```

**In [[Rust]] memory is returned to the allocator when its "owner" goes out of scope.**

When a variable goes out of scope,  [[Rust]] will call a special **drop** function to return the memory.

In [[C++]] this pattern of deallocating resources is called *[[Resource Acquisition Is Initialization (RAII)]]*.

## Ways variables and data inteact: Move