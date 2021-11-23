# securestack

A GitHub Action for using SecureStack to check for vulnerabilities in your GitHub projects. A different action is required depending on which language or build tool you are using. 

```
name: Example workflow using SecureStack
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Run SecureStack to check for vulnerabilities
        uses: securestack/actions/securestack@master
        env:
          SECURESTACK_API_KEY: ${{ secrets.SECURESTACK_API_KEY }}
```

Getting your SecureStack API Key

Continuing on error
Made with 💜 by SecureStack
