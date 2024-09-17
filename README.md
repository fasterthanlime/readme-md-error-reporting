
# This is a readme

With a code sample, that has an error:

```rust
fn main() {
    let x = 234 // no semicolon here! oh no!
}
```

At least with `rustc 1.83.0-nightly (c52c23b6f 2024-09-16)`, running doc-tests
results in error messages reported against `lib.rs`, not `README.md`:

```shell
readme-md-error-reporting on  main [?] is 📦 v0.1.0 via 🦀 v1.81.0
❯ cargo +nightly test --doc
    Finished `test` profile [unoptimized + debuginfo] target(s) in 0.00s
   Doc-tests readme_md_error_reporting

running 1 test
test src/lib.rs - (line 5) ... FAILED

failures:

---- src/lib.rs - (line 5) stdout ----
error: expected `;`, found `}`
 --> src/lib.rs:7:16
  |
3 |     let x = 234 // no semicolon here! oh no!
  |                ^ help: add `;` here
4 | }
  | - unexpected token
```

...but of course, this code is just above, in the Markdown! Not in lib.rs.
