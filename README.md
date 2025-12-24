# no-pico-args

![Build Status](https://github.com/drafteddev/no-pico-args/workflows/Rust/badge.svg)
[![Crates.io](https://img.shields.io/crates/v/no-pico-args.svg)](https://crates.io/crates/no-pico-args)
[![Documentation](https://docs.rs/no-pico-args/badge.svg)](https://docs.rs/no-pico-args)
[![Rust 1.32+](https://img.shields.io/badge/rust-1.31+-orange.svg)](https://www.rust-lang.org)
![](https://img.shields.io/badge/unsafe-forbidden-brightgreen.svg)

**`no_std` compatible version of [pico-args](https://github.com/RazrFalcon/pico-args).**

This is a fork of the popular [pico-args](https://github.com/RazrFalcon/pico-args) crate
by [RazrFalcon](https://github.com/RazrFalcon), with the goal of making it
`no_std` compatible. All the types (mainly `OsString` and `OsStr`) have been converted to `String` and `&str`
respectively, to make it `no_std` compatible. You will still need the `alloc` crate though.

One limitation this adds, is that it only supports UTF8 arguments.

See [pico-args](https://github.com/RazrFalcon/pico-args) for more information about the actual crate.

## Build features

- `std`

  Enables use of `std`-related functions.
  Disabling this will make the library `no_std` compatible.

- `eq-separator`

  Allows parsing arguments separated by `=`<br/>
  This feature adds about 1KiB to the resulting binary

- `short-space-opt`

  Makes the space between short keys and their values optional (e.g. `-w10`)<br/>
  If `eq-separator` is enabled, then it takes precedence and the '=' is not included.<br/>
  If `eq-separator` is disabled, then `-K=value` gives an error instead of returning `"=value"`.<br/>
  The optional space is only applicable for short keys because `--keyvalue` would be ambiguous

- `combined-flags`

  Allows combination of flags, e.g. `-abc` instead of `-a -b -c`<br/>
  If `short-space-opt` or `eq-separator` are enabled, you must parse flags after values,
  to prevent ambiguities

## Attribution

This crate is a fork of [pico-args](https://github.com/RazrFalcon/pico-args)
by [RazrFalcon](https://github.com/RazrFalcon) and does not really add any value to the original code, other than making
it `no_std` compatible. The entire logic is taken from the original crate, with only minor changes.

## License

MIT
