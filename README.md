# Jekyll GitHub Actions

A GitHub Action for building and deploying a Jekyll repo back to its `gh-pages` branch.

**Why not just let GitHub Pages build it? Because this way we can use our own custom Jekyll plugins and build scripts.**

## Secrets

- `GITHUB_TOKEN`: An access key which scoped to the repository - we need this to push the built site files back to the repo. This is generated for you on each workflow run——see usage in [example](#example). (GitHub Provides)
  
## Environment Variables

- `GITHUB_ACTOR`: Username of repo owner or object initiating the action (GitHub Provides)
- `GITHUB_REPO`: Owner/Repository (GitHub Provides)

## Example

```yml
name: Jekyll Deploy

on: [push]

jobs: 
  build_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Build & Deploy to GitHub Pages
        env: 
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          GITHUB_REPOSITORY: ${{ secrets.GITHUB_REPOSITORY }}
          GITHUB_ACTOR: ${{ secrets.GITHUB_ACTOR }}
        uses: BryanSchuetz/jekyll-deploy-gh-pages@master
```

Clones the repo, builds the site, and commits it back to the `gh-pages` branch of the repository. That's it. Just add the above example to a `main.yml` file in the `.github/workflows` directory of your repository—see caveats below.

## Caveats

- `destination:` should be set to `./build` in your `_config.yml` file—as God demands.
- A `Gemfile` is required. This must include `jekyll` and any other custom gems.

## References

1. <https://jekyllrb.com/docs/continuous-integration/github-actions/>
2. <https://github.com/helaili/jekyll-action>
3. <https://github.com/BryanSchuetz/jekyll-deploy-gh-pages>
4. <https://github.com/joshlarsen/jekyll4-deploy-gh-pages>
5. <https://github.com/alexcvcoelho/jekyll-deploy-gh-pages>
6. <https://github.com/David-Byrne/jekyll-diff-action>
