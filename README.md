# rsfc-action

Repository for hosting the RSFC action available in Github Marketplace

For more information on RSFC, you can visit its [Github repository](https://github.com/oeg-upm/rsfc)

## Previous considerations

The workflow that implements this action needs to have write permissions. Here's an example:

```
name: Run RSFC analysis

on:
  push:

permissions:
  checks: write
  contents: read

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run local action
        uses: ./
        with:
          repo_url: https://github.com/${{ github.repository }}
          is_fork: "false"
          pr_sha: ${{ github.sha }}
```


