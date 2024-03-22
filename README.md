# Github Action running git-crypt unlock

## Usage

### Example Workflow file

```yaml
jobs:
  deploy:
    name: unlcok repo secrets
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Unlock secrets
        uses: biessek/github-action-git-crypt-unlock@1.0.0
        with:
            unlock-key: {{ secrets.GIT_CRYPT_SECRET }}
```

### Parameters

- `unlock-key` **Required** Base64 encoded git-crypt key file.
  - Get it from an unlocked git-crypt env with:
    ```sh
    git-crypt export-key ./tmp-key && cat ./tmp-key | base64 | pbcopy && rm ./tmp-key
    ```