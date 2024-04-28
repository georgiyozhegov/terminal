<div align="center">
    <img src="https://github.com/georgiyozhegov/terminal/assets/159022025/b9bf9c24-486c-44b1-ac9e-e856426c2acc" width=240px height=240px>
    <h1 align="center">Ruterm</h1>
    <p align="center">Tiny library for working with the terminal</p>
    
[![docs.rs](https://img.shields.io/docsrs/ruterm)](https://crates.io/crates/ruterm)
![GitHub License](https://img.shields.io/github/license/georgiyozhegov/terminal)
</div>

# Installation
```bash
cargo add ruterm # from crates.io
```
```bash
cargo add --git https://github.com/georgiyozhegov/terminal.git # more recent version
```

# Usage
```rust
use ruterm::{
    error::Result,
    in_raw,
    style::{color::fore, RESET},
    io::write,
    size,
    cursor,
};

fn main() -> Result<()> {
    in_raw!({
        cursor::start()?; // clear screen
        let (w, h) = size()?;
        cursor::set(w / 2, h / 2)?; // move cursor to the center
        write(fore::GREEN.as_bytes())?; // green foreground
        write(b"Hello from raw mode!\n\r")?;
        write(RESET.as_bytes())?; // reset style
        cursor::set(0, h)?; // move cursor to the bottom
    });

    Ok(())
}
```

# Examples
```bash
cargo run --example car
```
[example](https://github.com/georgiyozhegov/terminal/assets/159022025/e4c4beff-a252-425a-a6c8-a976a327c88d)
