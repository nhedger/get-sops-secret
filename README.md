# Get SOPS secret in GitHub Actions

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/nhedger/get-sops-secret?label=latest&logo=github)](https://github.com/marketplace/actions/get-sops-secret)
[![Test](https://github.com/nhedger/get-sops-secret/actions/workflows/test.yaml/badge.svg)](https://github.com/nhedger/get-sops-secret/actions/workflows/test.yaml)

This actions provides a straightforward way to get a single secret from a SOPS encrypted file
and outputs it as a GitHub Actions output.

## Inputs

The following inputs are supported.

```yaml
- name: Get SOPS secret
  uses: nhedger/get-sops-secret@v1
  with:

    # Path to the SOPS encrypted file that contains the secret.
    # Required.
    secrets-file: /path/to/secrets.yaml

    # Name of the secret to retrieve
    # Required.
    secret-name: my-secret

    # AGE private key
    # Required.
    age-private-key: ${{ secrets.AGE_PRIVATE_KEY }}

    # SOPS version to use for decrypting the file.
    # Optional.
    # Default: latest
    sops-version: latest
```

## Outputs

This actions returns single `secret` output with the value of the secret.

## Example

```yaml
- name: Get SOPS secret
  uses: nhedger/get-sops-secret@v1
  id: get-secret
  with:
    secrets-file: /path/to/secrets.yaml
    secret-name: my-secret
    age-private-key: ${{ secrets.AGE_PRIVATE_KEY }}

- name: Print secret
  run: echo ${{ steps.get-secret.outputs.secret }}
```

## License

The scripts and documentation in this project are licensed under
the [MIT License](LICENSE.md).