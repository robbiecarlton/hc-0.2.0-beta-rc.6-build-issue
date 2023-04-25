# hc-0.2.0-beta-rc.6-build-issue

This is a minimal reproduction of an issue I'm running into building with holochain `0.2.0-beta-rc.6`

To reproduce just run

```
nix develop
cargo build
```

You should see the following errror

```
error[E0308]: mismatched types
   --> /Users/robbie/code/holo/scaffolding/.cargo/registry/src/github.com-1ecc6299db9ec823/holochain-0.2.0-beta-rc.6/src/sweettest/sweet_conductor_config_rendezvous.rs:101:17
    |
101 |             let (sig_addr, sig_driver) = tx5_signal_srv::exec_tx5_signal_srv(sig_conf).unwrap();
    |                 ^^^^^^^^^^^^^^^^^^^^^^   ------------------------------------------------------ this expression has type `(Pin<Box<dyn futures::Future<Output = ()> + std::marker::Send>>, Vec<std::net::SocketAddr>, Vec<std::io::Error>)`
    |                 |
    |                 expected a tuple with 3 elements, found one with 2 elements
    |
    = note: expected tuple `(Pin<Box<dyn futures::Future<Output = ()> + std::marker::Send>>, Vec<std::net::SocketAddr>, Vec<std::io::Error>)`
               found tuple `(_, _)`
```
