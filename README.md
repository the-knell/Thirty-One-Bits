# Thirty-One Bits

**knell**

Timestamp of record (archive.org): https://archive.org/details/knell-thirty-one-bits

InfiniteWP Client 1.13.10 — a WordPress management plugin on roughly 200,000 installs — has a second authentication branch, NOSSL, that the enrolling panel selects by setting one request parameter, even on hosts that could use RSA. Once selected, the branch is permanent and its signing key is generated as the MD5 of the panel's **public** key concatenated with a single `rand()` result: no more than 2^31 of secret, over a prefix anyone can know. The signature covers only action and message ID; parameters are never signed, and captured requests replay with mutated parameters. Proven live against our own instance: from one captured request and the panel's public key, the key was recovered offline in 291.9 seconds and a forged state-changing command was accepted — unrestricted, permanent forgery of the site's management channel. The paper does not claim all 200,000 installs are NOSSL-enrolled; the enrolled share is not externally measurable. This is the first publication of this construction known to the record.

## Verify

```
gpg --import knell-public.asc
gpg --verify paper-infinitewp-FINAL-2026-11-04.md.asc
```

Expect: `Good signature from "knell"`, key 133883AB9F6EDE5B9BA6B82E27BEDAF0CE152F25
Fingerprint: 1338 83AB 9F6E DE5B 9BA6 B82E 27BE DAF0 CE15 2F25
