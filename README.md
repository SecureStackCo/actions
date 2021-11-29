# SecureStack GitHub Actions

A set of GitHub Actions for using SecureStack to analyse an application and the constituent codebase for application attack surface (exposure), software composition (code) and secret vulnerabilities.

```
name: Example Workflow Using SecureStack Actions
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo for running secrets analysis within workflow
        id: checkout
        uses: actions/checkout@v2.4.0
        with:
          fetch-depth: 0
      - name: Exposure Analysis Step
        id: exposure
        uses: NiftyBank/niftybank-app/actions/exposure@master
        with:
          securestack_api_key: ${{ secrets.SECURESTACK_API_KEY_SECRET }}
          securestack_app_id: ${{ secrets.SECURESTACK_APPI_ID }}
          severity: critical
          flags: '--dom'
      - name: SCA Analysis Stepp
        id: code
        uses: NiftyBank/niftybank-app/actions/code@master
        with:
          securestack_api_key: ${{ secrets.SECURESTACK_API_KEY_SECRET }}
          securestack_app_id: ${{ secrets.SECURESTACK_APPI_ID }}
          severity: critical
          language: node
      - name: Secrets Analysis Step
        id: secrets
        uses: NiftyBank/niftybank-app/actions/secrets@master
        with:
          securestack_api_key: ${{ secrets.SECURESTACK_API_KEY_SECRET }}
          securestack_app_id: ${{ secrets.SECURESTACK_APPI_ID }}
          severity: critical
          flags: '-d 50'

```

## Getting your SecureStack API Key

TODO

Made with 💜 by SecureStack
