# Push GitHub Actions

```yaml
# push.yaml

permissions: write-all

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
      with:
        persist-credentials: false # otherwise, the token used is the GITHUB_TOKEN, instead of your personal token
        fetch-depth: 0 # otherwise, you will failed to push refs to dest repo
    - name: Create local changes
      run: |
        ...
    - name: Commit files
      run: |
        git config --local user.email "41898282+github-actions[bot]@users.noreply.github.com"
        git config --local user.name "github-actions[bot]"
        git add -A
        git commit -m -a "Add changes" || true
        # The above command will fail if no changes were present, so we ignore
        # the return code.
    - name: Push changes
      uses: tianheg/github-actions@push
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        branch: ${{ github.ref }}
```

---

**References**:

1. [ad-m/github-push-action](https://github.com/ad-m/github-push-action)
