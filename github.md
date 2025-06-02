# GitHub

## Secrets

- View a secret vlaue in GitHub Actions

  ```yaml
  - run: |
        echo ${{secrets.secret_name}} | sed 's/./& /g'`
  ```
