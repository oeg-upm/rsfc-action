# rsfc-action

Repository for hosting the RSFC action available in Github Marketplace. For more information on RSFC, you can visit its [Github repository](https://github.com/oeg-upm/rsfc)

## Previous considerations

The workflow that implements this action needs to have write permissions. Here's an example:

```
name: Run RSFC analysis

on:
  workflow_dispatch: 
  pull_request: 
    types: [opened, synchronize, reopened]

permissions:
  permissions:
  checks: write
  contents: read

jobs:
  run-rsfc-checks:
    uses: oeg-upm/rsfc-action@v1
    with:
      repo_url: https://github.com/${{ github.repository }}
      is_fork: ${{ github.event.pull_request.head.repo.full_name != github.repository }}
      pr_sha: ${{ github.event.pull_request.head.sha }}
    secrets:
      RSFC_TOKEN: ${{ secrets.RSFC_TOKEN }}  
```


