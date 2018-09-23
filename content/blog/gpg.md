+++
title = "Managing stripped GPG keys"
date = 2017-12-03

[taxonomies]
tags = ["gpg", "security"]
+++

```
    +--(master pass)                   +----(user pass)--+
    |        |                         |                 |
    |     decrypts                 decrypts           decrypts
    |        |                         |                 |
    |        v                         v                 v
decrypts  +----------------+     +----------+      +-----------+
    |     | TRUSTED        |     | ANDROID  |      | KEYCHAIN  |
    |     | SCA (master)   |     | SE (ssb) |      | SEA (ssb) |
    |     | offline + HSM  |     | Sandbox  |      | HSM       |
    |     +----------------+     +----------+      +-----------+
    |          |                        ^                 ^
    |          |                        |                 |
    |          +----creates-------------|-----------------+
    |
    |  +-----------------+
    |  | PAPER           |
    +->| SEA (master)    |
       | remote on paper |
       +-----------------+
```

See [here](https://www.void.gr/kargig/blog/2013/12/02/creating-a-new-gpg-key-with-subkeys/) on how to strip the master key (sec) from your keyring and create secret subkeys (ssb) for daily active use.
The master key can sign (S) new subkeys, create certificates (C) and provide authentication (A).
The master key lives forever, while the ssb that is used for signing is created with an expiration date.
All encryption keys may remain valid indefinitely until revoked.
The master key can be used to revoke the subkeys.

A few considerations

- use a separate PIN on the trusted system / for the master key (sec) in case a key-logger reads the PIN on a semi-trusted machine (e.g. laptop or android) when decrypting a secret subkey (ssb)
- use subkey (A) for authenticating ssh
- keep master key offline / air-gapped
