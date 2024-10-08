# unicode-normalization

[![Build Status](https://travis-ci.org/unicode-rs/unicode-normalization.svg)](https://travis-ci.org/unicode-rs/unicode-normalization)
[![Docs](https://docs.rs/unicode-normalization/badge.svg)](https://docs.rs/unicode-normalization/)

Unicode character composition and decomposition utilities
as described in
[Unicode Standard Annex #15](http://www.unicode.org/reports/tr15/).

This crate requires Rust 1.36+.

```rust
extern crate unicode_normalization;

use unicode_normalization::char::compose;
use unicode_normalization::UnicodeNormalization;

fn main() {
    assert_eq!(compose('A','\u{30a}'), Some('Å'));

    let s = "ÅΩ";
    let c = s.nfc().collect::<String>();
    assert_eq!(c, "ÅΩ");
}
```

## crates.io

You can use this package in your project by adding the following
to your `Cargo.toml`:

```toml
[dependencies]
unicode-normalization = "0.1.24"
```

## `no_std` + `alloc` support

This crate is completely `no_std` + `alloc` compatible. This can be enabled by disabling the `std` feature, i.e. specifying `default-features = false` for this crate on your `Cargo.toml`.

## Note about MSRV

Dependencies' MSRVs evolve independently, and cargo will always try to get the most recent versions.
Therefore, if you are having troubles compiling on an old Rust version, try to install an older version of the incompatible dependency.

For instance, to compile on Rust 1.36, `tinyvec` must be `<=1.6.0`
```sh
cargo update -p tinyvec --precise 1.6.0
```
