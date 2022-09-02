[[Variables]] are by default immutable in rust. Once a value is bound to a name, you can't change that value.

For example: 

```rust
fn main() {
	let x = 5;
	println!("The value of x is: {x}");
	x = 6;
	println!("The value of x is: {x}");
}
```

The above code will error since you can't assign twice to an [[immutable]] variable.

Adding `mut` to the [[variable]] declaration (such as `let mut x = 5;`) allows the variable to be changed after assignment.

## Constants

[[Constants]] in [[Rust]] are always immutable. They are declared using the `const` keyword:

`const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;`

Constants are valid for the entire time the program runs within the scope they were declared in. In this sense they can be treated as having a [[static lifetime]].

## Shadowing

While you cannot change the value of an immutable variable, you **CAN** reassign said variable to overshadow the value it took before.

This concept is called [[shadowing]] in [[Rust]]:

```rust
fn main() {
	let x = 5;

	let x = x + 1;

	{
		let x = x * 2;
		println!("The value of x in the inner scope is: {x}");
	}

	println!("The value of x is: {x}");
}
```
 
The code above will output: 

```
The value of x in the inner scope is: 12 The value of x is: 6
```

[[Shadowing]] retains the property of immutable variables in that they cannot be changed, while still providing a way to transform the value. This is because we're effectively creating a new variable and moving the old one out of scope.

[[Shadowing]] is particularly useful when you want to get a property of a value that should be immutable (like a string, for instance) without having to declare multiple variables.

```rust
let characters = "I am a string!";
let characters = characters.len();
```