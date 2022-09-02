# Functions in Rust

Rust uses [[snake case]] as the conventional style for function and variable names.

```rust
fn main() {
	println!("Main function.")

	another_function(44);
}

fn another_function(value: i32) {
	println!("Some value: {value}");
}
```

In function signatures you ***must*** provide the type for each parameter. 

## Statements and expressions

[[Rust]] is an expression based languaged. Functions are made up of a series of statements, and optionally end in an expression.

***Statements* are instructions that perform some action and do not return a value.**

***Expressions* evaluate to a resulting value.**

`let y = 6;` is a statement.

```rust
fn main() {
	let y = 6;
}
```

Function definitions are also statements.

Since statements don't return anything, you can't assign a `let` statement to another variable such as `let x = (let y = 6);` (this will error with "variable declaration using `let` is a statement")

This is different from other languages where an assignment returns the value of the assignment and you can do stuff like `x = y = 6`.

Expressions make up the majority of code written in [[Rust]]. Calling a function is an expression. Calling a macro is an expression. Evaluating a new scope block is an expression:

```rust
fn main() {
	let y = {
		let x = 3;
		x + 1
	}
}
```

Expressions do not include ending semicolons. If you hadd a semicolon to the end of an expression it turns into a statement. **Turning an expression into a statement will cause it to not return a value.**

## Functions with return values

In [[Rust]] the return value of a function is synonymous with the value of the final expression in the block of a body of a function.

Return values of functions are annotated with `->`:

```rust
fn five() -> i32 {
	5
}
```

Function expressions are evaluated with the last value in the function scope (like above) unless explicitly returned from with a `return` statement.