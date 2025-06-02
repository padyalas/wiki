# GitHub

## Secrets

- View a secret vlaue in GitHub Actions
  - `run: |
        echo ${{secrets.secret_name}} | sed 's/./& /g'`
