# Vendor Base64

This is a simple Base64 implementation in rust.  
It is meant to be copied into your rust project.  
It cannot be installed from crates.io.  

This is based on [RFC 4648](https://datatracker.ietf.org/doc/html/rfc4648)

## Padding

`encode()` includes padding.  
`decode()` supports padding and no padding.

## How to Use

1. Copy `base64.rs` into your project
1. Add `pub mod base64;` into your `lib.rs`
1. Use `base64::encode()` and `base64::decode()`
1. See [docs](https://andrew-shay.github.io/rust_vendor_base64/vendor_base64/base64/index.html)

```rust
use vendor_base64::base64;  // Replace vendor_base64 with your project name

// Encode
let bytes = "rust".as_bytes();
let encoded = base64::encode(bytes);
assert_eq!(encoded, "cnVzdA==");

// Decode
let decoded = base64::decode(&encoded).unwrap();
assert_eq!(decoded, bytes);

// Decode without padding
let decoded = base64::decode("cnVzdA").unwrap();
assert_eq!(decoded, bytes);
```

## Why Use This?

You don't want the API to suddenly break.  
You just want the standard Base64 encode/decode.  
You want to remove a dependency that is downloaded from crates.io.  

## Limitations

There is no:

1. URL safe encode
1. Encode without padding
1. Custom alphabet support

## Compared to the crates.io base64 crate

This implementation seems to be about 2-4x slower than the [base64 crate](https://docs.rs/base64/latest/base64/).  ~50ms vs ~16ms in some simple tests.

base64 crate has more features.

## Tests

Run `$ cargo test`  

## Docs

See [docs](https://andrew-shay.github.io/rust_vendor_base64/vendor_base64/base64/index.html)  

Run `$ cargo doc --open`

# License

MIT-0