# DomoticASW semantic release

This action is meant to be used across all the suitable repositories inside the organization.

It automatically checks out the repository and setup Node.

## Requirements:
The repository should have [semantic-release](https://www.npmjs.com/package/semantic-release) installed and configured (you should be able to run `npx semantic-release`).

Using this action in another job requires permissions and the github token as showed below:

```yaml
# ...
jobs:
  release:
    name: ...
    runs-on: ...
    permissions:
      contents: write # to be able to publish a GitHub release
      issues: write # to be able to comment on released issues
      pull-requests: write # to be able to comment on released pull requests
      id-token: write # to enable use of OIDC for npm provenance
    steps:
      - name: semantic-release
        uses: DomoticASW/semantic-release@1.0.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```
