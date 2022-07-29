# FAQ

cargo build --> Permission denied

```
cargo build
error: failed to create directory `/home/dau/workspace/network/CosmWasm/astroport/astroport-dca/target/debug`

Caused by:
  Permission denied (os error 13)

--------------------------------
https://github.com/rust-lang/cargo/issues/6757
Solution:
sudo chown -R $(whoami) /home/dau/workspace/network/CosmWasm/astroport/astroport-dca/

```
