# ID Capture Releases

Official public release repository for ID Capture macOS application binaries and
update metadata.

This repository does not contain the application source code. It is used by the
ID Capture app to check whether a newer macOS build is available.

## Structure

```text
app/
  macos/
    latest.json
    1.0.6/
      manifest.json
      ID-Capture-1.0.6.zip
```

`latest.json` points to the newest release manifest. Each version folder contains
metadata for that release and the matching zipped app build.

## Update URL

The app checks:

```text
https://raw.githubusercontent.com/miha-xgroup/ID-Capture-Releases/main/app/macos/latest.json
```

## Publishing A Release

1. Build and archive ID Capture.
2. Zip the signed `ID Capture.app` as `ID-Capture-VERSION.zip`.
3. Place the zip in `app/macos/VERSION/`.
4. Calculate the SHA-256 checksum:

```sh
shasum -a 256 app/macos/VERSION/ID-Capture-VERSION.zip
```

5. Update `app/macos/VERSION/manifest.json`.
6. Update `app/macos/latest.json`.
7. Commit and push.
