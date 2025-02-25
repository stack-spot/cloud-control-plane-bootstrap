# cloud-control-plane-bootstrap

Github Action to download Stackspot cloud control plane bootstrap module.

_**Note**: This action is supported on all runners operating systems (`ubuntu`, `macos`, `windows`)_

## 📚 Usage

### Requirements

To get the account keys (`CLIENT_ID`, `CLIENT_KEY` and `CLIENT_REALM`), please login using a **ADMIN** user on the [StackSpot Portal](https://stackspot.com), and generate new keys at [https://stackspot.com/en/settings/access-token](https://stackspot.com/en/settings/access-token).

### Use Case

```yaml
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4.2.1
      - name: Download control plane bootstrap ZIP file
        id: download
        uses: stack-spot/cloud-control-plane-bootstrap@v1
        with:
          CLIENT_KEY: ${{ secrets.CLIENT_KEY }}
          CLIENT_ID: ${{ secrets.CLIENT_ID }}
          REALM: ${{ secrets.CLIENT_REALM }}
          VERSION: "latest" # Optional, defaults to "latest"
          DOWNLOAD_FOLDER: "./downloads"
      - name: Verify bootstrap ZIP file
        run: |
          echo "Downloaded ZIP file path: ${{ steps.download.outputs.ZIP_PATH }}"
        shell: bash
```

* * *

## ▶️ Action Inputs

Field | Mandatory | Default Value | Observation
------------ | ------------  | ------------- | -------------
**CLIENT_ID** | YES | N/A | [StackSpot](https://stackspot.com/en/settings/access-token) Client ID.
**CLIENT_KEY** | YES | N/A |[StackSpot](https://stackspot.com/en/settings/access-token) Client KEY.
**CLIENT_REALM** | YES | N/A |[StackSpot](https://stackspot.com/en/settings/access-token) Client Realm.
**VERSION** | NO | `latest` | Bootstrap version.
**DOWNLOAD_FOLDER** | NO | `GITHUB_WORKSPACE` | Folder when the boostrap zip file will be downloaded.

## ▶️ Action output

Field | Observation
------------ | ------------
**ZIP_PATH** | Path to the downloaded ZIP file.

* * *

## License

[Apache License 2.0](https://github.com/stack-spot/cloud-deploy-action/blob/main/LICENSE)
