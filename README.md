# forksync
Code to keep forked repository sync with GitHub Actions.

## Use case
With this library, for example, you can have a code base maintained by an organization mirrored in a personal account, so that the code is automatically synchronized between these two repositories.

## Use example 

```yaml

# .github/workflows/syncfork.yml

name: Sync fork repo
on:
  push:
    branches: [main]

jobs:
  fork_sync:
    runs-on: ubuntu-latest
    name: Sync fork repo

    steps:
      - name: Fetch and merge upstream
        if: ${{ github.repository == 'REPOSITORY NAME HERE WITH SINGLE QUOTES'}}
        uses: aquelegustavo/forksync@v1.4
        with:
          UPSTREAM_USER: josealexandrecom #Example: Organization name
          UPSTREAM_REPO: website #Example: Organization repository
          FORKED_USER: botjam #Example: Your account
          FORKED_REPO: website #Example: Your copy repository
          USER_TOKEN: ${{secrets.WEBSITE_SYNC_FORK_BOTJAM_TOKEN}} #Your personal acess token
          
```

## Credits
Make with ❤️ by Gustavo Simões
