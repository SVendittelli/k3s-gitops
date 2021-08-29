# k3s GitOps

[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow)](https://conventionalcommits.org)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)

Configuration for my personal `k3s` cluster. Deployed and managed using [flux](https://fluxcd.io).

## :warning: pre-commit

It is advisable to install [pre-commit](https://pre-commit.com/) and the pre-commit hooks that come with this repository.
[sops-pre-commit](https://github.com/k8s-at-home/sops-pre-commit) will check to make sure you are not by accident commiting your secrets un-encrypted.

After pre-commit is installed on your machine run:

```sh
pre-commit install -t pre-commit -t commit-msg --install-hooks
```

## :closed_lock_with_key: Flux SOPS integration

GPG encrypted secrets using [SOPS](https://github.com/mozilla/sops) can be committed directly as they will be [decrypted when deployed by flux](https://fluxcd.io/docs/guides/mozilla-sops). Use the following command to encrypt plain text secrets. The public key is included for encrypting new secrets. Git diffs can be shown in plain text by [configuring git correctly](https://github.com/mozilla/sops#showing-diffs-in-cleartext-in-git).

```sh
sops --encrypt --in-place ./cluster/<SECRET_NAME>.sops.yaml
```
