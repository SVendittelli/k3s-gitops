# k3s GitOps

Configuration for my personal `k3s` cluster. Deployed and managed using [flux](https://fluxcd.io).

## Flux SOPS integration

GPG encrypted secrets using [SOPS](https://github.com/mozilla/sops) can be committed directly as they will be [decrypted when deployed by flux](https://fluxcd.io/docs/guides/mozilla-sops). Use the following command to encrypt plain text secrets. The public key is included for encrypting new secrets. Git diffs can be shown in plain text by [configuring git correctly](https://github.com/mozilla/sops#showing-diffs-in-cleartext-in-git).

```sh
sops --encrypt --in-place ./cluster/<SECRET_NAME>.sops.yaml
```
