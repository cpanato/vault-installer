# vault-installer GitHub Action

This action enables you to install [Hashicorp Vault](https://developer.hashicorp.com/vault).

## Usage

This action currently supports GitHub-provided Linux, macOS and Windows runners (self-hosted runners may not work).

Add the following entry to your Github workflow YAML file:

```yaml
uses: cpanato/vault-installer@main
with:
  vault-release: '1.12.1' # optional
```

Example using a pinned version:

```yaml
jobs:
  test_cosign_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install Vault and test presence in path
    steps:
      - name: Install Vault
        uses: cpanato/vault-installer@main
        with:
          vault-release: '1.12.1'
      - name: Check install!
        run: vault version
```

Example using the default version:

```yaml
jobs:
  test_cosign_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install Vault and test presence in path
    steps:
      - name: Install Vault
        uses: cpanato/vault-installer@main
      - name: Check install!
        run: vault version
```


### Optional Inputs

The following optional inputs:

| Input | Description |
| --- | --- |
| `vault-release` | `vault` version to use instead of the default. |
| `install-dir` | directory to place the `vault` binary into instead of the default (`$HOME/.vault`). |
| `use-sudo` | set to `true` if `install-dir` location requires sudo privs. Defaults to false. |
