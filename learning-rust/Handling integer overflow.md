[[Rust]] checks for [[integer overflow]] at runtime and will cause the program to panic. When compiling in release mode (with `--release` flag) [[Rust]] **does not** cause panics. Instead it will perform [[two's complement]] wrapping. Relying on this behaviour is considered an error.

Explicitly handle [[integer overflow]] in [[Rust]] by wrapping via standard library `wrapping_*` such as `wrapping_add` or return `None` if there is overflow with the `checked_*` methods.
