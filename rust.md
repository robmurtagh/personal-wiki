# Rust

## Installation

Install [rustup](https://github.com/rust-lang-nursery/rustup.rs):

```bash
brew install rustup-init
rustup-init
```

Install [Rust Language Server](https://github.com/rust-lang-nursery/rls):

```bash
rustup update
rustup component add rls-preview rust-analysis rust-src
```

Install the [Rust Language Server VSCode extension](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust)

## Hello World

From [Rust by Example](https://doc.rust-lang.org/rust-by-example/):

```rust
// hello.rs
fn main() {
    println!("Hello World!");
}
```

```bash
rustc hello.rs
./hello
```

## Packaging etc

- Packaging is done with [Cargo](https://doc.rust-lang.org/cargo/index.html)
- Each distributed package is called a Crate
- The primary Crate registry is [Crates.io](https://crates.io/)
- A simple starting guide is [here](https://doc.rust-lang.org/cargo/getting-started/first-steps.html)

To create a new project, then compile and run it:

```bash
cargo new rust_example
cd rust_example
cargo run
```

- [Add dependencies](https://doc.rust-lang.org/cargo/guide/dependencies.html) to Cargo.toml