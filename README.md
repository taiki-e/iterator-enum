# iter-enum

[![crates-badge]][crates-url]
[![docs-badge]][docs-url]
[![license-badge]][license]
[![rustc-badge]][rustc-url]

[crates-badge]: https://img.shields.io/crates/v/iter-enum.svg
[crates-url]: https://crates.io/crates/iter-enum
[docs-badge]: https://docs.rs/iter-enum/badge.svg
[docs-url]: https://docs.rs/iter-enum
[license-badge]: https://img.shields.io/badge/license-Apache--2.0%20OR%20MIT-blue.svg
[license]: #license
[rustc-badge]: https://img.shields.io/badge/rustc-1.31+-lightgray.svg
[rustc-url]: https://blog.rust-lang.org/2018/12/06/Rust-1.31-and-rust-2018.html

\#\[derive(Iterator, DoubleEndedIterator, ExactSizeIterator, Extend)\] for enums.

## Usage

Add this to your `Cargo.toml`:

```toml
[dependencies]
iter-enum = "0.2"
```

The current iter-enum requires Rust 1.31 or later.

## Examples

```rust
use iter_enum::*;

#[derive(Iterator, DoubleEndedIterator, ExactSizeIterator, FusedIterator, Extend)]
enum Either<A, B> {
    A(A),
    B(B),
}

fn foo(x: i32) -> impl Iterator<Item = i32> {
    if x > 0 {
        Either::A(x..=0)
    } else {
        Either::B(Some(x).into_iter())
    }
}
```

See [auto_enums](https://github.com/taiki-e/auto_enums) crate for how to automate patterns like this.

## Supported traits

* [`Iterator`](https://doc.rust-lang.org/std/iter/trait.Iterator.html) - [generated code](doc/iterator.md)
* [`DoubleEndedIterator`](https://doc.rust-lang.org/std/iter/trait.DoubleEndedIterator.html) - [generated code](doc/double_ended_iterator.md)
* [`ExactSizeIterator`](https://doc.rust-lang.org/std/iter/trait.ExactSizeIterator.html) - [generated code](doc/exact_size_iterator.md)
* [`FusedIterator`](https://doc.rust-lang.org/std/iter/trait.FusedIterator.html) - [generated code](doc/fused_iterator.md)
* [`Extend`](https://doc.rust-lang.org/std/iter/trait.Extend.html) - [generated code](doc/extend.md)
* [`TrustedLen`](https://doc.rust-lang.org/std/iter/trait.TrustedLen.html) - [generated code](doc/trusted_len.md) (*requires `"trusted_len"` feature*)
* [`ParallelIterator`](https://docs.rs/rayon/1/rayon/iter/trait.ParallelIterator.html) - [generated code](doc/parallel_iterator.md) (*requires `"rayon"` feature*)
* [`IndexedParallelIterator`](https://docs.rs/rayon/1/rayon/iter/trait.IndexedParallelIterator.html) - [generated code](doc/indexed_parallel_iterator.md) (*requires `"rayon"` feature*)
* [`ParallelExtend`](https://docs.rs/rayon/1/rayon/iter/trait.ParallelExtend.html) - [generated code](doc/parallel_extend.md) (*requires `"rayon"` feature*)

## Related Projects

* [auto_enums]: A library for to allow multiple return types by automatically generated enum.
* [derive_utils]: A procedural macro helper for easily writing [derives macros][proc-macro-derive] for enums.
* [futures-enum]: \#\[derive(Future, Stream, Sink, AsyncRead, AsyncWrite, AsyncSeek, AsyncBufRead)\] for enums.
* [io-enum]: \#\[derive(Read, Write, Seek, BufRead)\] for enums.

[auto_enums]: https://github.com/taiki-e/auto_enums
[derive_utils]: https://github.com/taiki-e/derive_utils
[futures-enum]: https://github.com/taiki-e/futures-enum
[io-enum]: https://github.com/taiki-e/io-enum

## License

Licensed under either of [Apache License, Version 2.0](LICENSE-APACHE) or [MIT license](LICENSE-MIT) at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.
