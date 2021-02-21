# ENet library in Rust, modified for Growtopia

This is a modified version of the [enet-rs](https://github.com/futile/enet-rs) library that works with Growtopia's new protocol.

## Usage

This will not be uploaded to crates.io, so to use it in your project, you will have to include the git path as a dependency:

```toml
[dependencies]
enet = { git = "https://github.com/ReimarPB/growtopia-enet-rs" }
```

## Changes

[ENet::create_host](https://docs.rs/enet/0.2.3/enet/struct.Enet.html#method.create_host) has an extra parameter: `using_new_packet`. If this is set to true, it will use Ubisoft's new modified protocol.

### Example

```rust
let mut host = enet.create_host::<()>(
    None,
    1,
    ChannelLimit::Maximum,
    BandwidthLimit::Unlimited,
    BandwidthLimit::Unlimited,
    true // Uses Growtopia's new protocol
).unwrap();
```

### Notes

* To connect to the official Growtopia servers, `using_new_packet` must be set to true.
* If a server has this set to true, the `server_data.php` file must have this line added to it: `type2|1`
* Documentation for the original library can be found [here](https://docs.rs/enet/0.2.3/enet/index.html).
