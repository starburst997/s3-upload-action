# s3-upload-action
Simple upload to S3 with rotating version folders

This was made for a simple use-case. Let's say you upload the content of a folder somewhere in S3 which are named after a version (ex; `2025.12.145`) and you want to keep only the latest 5 releases.

**Works only on linux runner** (maybe macos as well).

## Secrets:

TODO: How to get access key in AWS... Simple guide.

## Usage:

```yml
- name: Upload folder but keep the latest 5 only
  uses: starburst997/s3-upload-action@v1
  with:
    key-id: ${{ secrets.S3_KEY_ID }}
    secret-access-key: ${{ secrets.S3_SECRET_ACCESS_KEY }}
    region: ${{ secrets.S3_REGION }}
    endpoint: ${{ secrets.S3_ENDPOINT }}
    bucket: ${{ secrets.S3_BUCKET }}

    src-dir: 'my/folder/to/upload'
    dst-dir: 'apps/test/internal/windows'
    dst-version: '2025.1.12'
    keep: 5
```