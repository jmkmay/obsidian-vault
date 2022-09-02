# Control flow in Rust

[[Rust]] supports various expressions; some familiar, and some unique to the language.

## `if` expressions

`if` expressions expect an [[Boolean]] value when evaluating its control flow.

`if/else` statements work as expected:

```rust
let number = 6;

if number % 4 == 0 {
	println!("number is divisible by 4");
} else if number % 3 == 0 {
	println!("number is divisible by 3");
} else if number % 2 == 0 {
	println!("number is divisible by 2");
} else {
	println!("number is not divisible by 4, 3, or 2");
}
```

Since `if` is an expression (returns `true` or `false` ), it can be used in a `let` statement: 

```rust
fn main() {
	let condition = true;
	let number = if condition { 5 } else { 6 };
}
```

In above case, `number` will be bound to a value depending on `condition`.

All possible values that can be assigned to `number` must be of the same type.

## Controlling repetition with loops

[[Rust]] has three kinds of loops: `loop`, `while`, and `for`.

### `loop`

`Loop` will execute a block of code until you explicitly tell it to stop.

```rust
fn main() {
	let mut x = 0;
	loop {
		if x == 4 {
			break
		}
		x = x + 1;
	}

	let mut y = 0;
	loop {
		y = y + 1;
		if y != 4 {
			continue
		}
		break
	}
}
```

Since `loop` is an expression, you can return values from it. 

One such use case if in a retry operation. You can pass the result of a retry loop to the outer scope of the `loop`.

```rust
fn main() {
	let mut retry_counter = 0;

	let result = loop {
		retry_counter = retry_counter + 1;

		if counter == 10 {
			break counter * 2;
		}
	}

	println!("Result from retry: {result}")
}
```

You can label your loops to break from a specific loop:

```rust
fn main() {
	let mut count = 0;

	'counting_up': loop {
		println!("count = {count}");
		let mut remaining = 10;

		loop {
			println!("remaining = {remaining}");
			if remaining == 9 {
				break;
			}
			if count == 2 {
				break 'counting_up';
			}
			remaining = remaining - 1;
		}

		count = count + 1;
	}

	println!("End count = {count}");
}
```

This is a [[very useful feature of Rust]].

### `while`

Like most other programming languages, `while` will evaluate a block of code while a condition holds true:

```rust
while number != 0 {
	println!("{number}");

	number -= 1;
}
```

`for` 

A concise alternative to `while` for looping through a collection is `for`.

`for` will execute some code on each item in a collection:

```rust
for element in a {
	println!("the value is {element}")
}
```

[[Rust]] promotes using `for` loops whenever possible, since they are less error prone than `while`. Even for doing things a fixed number of times, `for` can be used in conjunction with `Range` and various other standard library tools to safely perform various control schemes:

```rust
fn main() {
	for number in (1..4).rev() { // will produce [4, 3, 2, 1]
		println!("{number}")
	}
	println!("liftoff!!!")
}
```



