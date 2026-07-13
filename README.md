# ShariahCalc

Static assets and tooling for the ShariahCalc project.

## Contents

- **`zakat_funds_tutorial.html`** — A self-contained, interactive Arabic (RTL) tutorial
  on Zakat for investment funds (زكاة الصناديق الاستثمارية). All fonts, styles, and
  scripts are inlined, so it can be served or opened directly with no build step and no
  external dependencies.

## Deploying the tutorial

The HTML file is fully self-contained. To publish it you can:

- Open it directly in a browser (`file://`), or
- Serve it from any static host (Firebase Hosting, GitHub Pages, S3, nginx, etc.).

Example, if you use Firebase Hosting:

```bash
# from the repo root, with the Firebase CLI installed and authenticated
firebase deploy --only hosting
```

## Secrets & credentials — important

**No credentials are stored in this repository, by design.**

A Firebase Admin SDK **service account key** was provided alongside these assets. It was
**intentionally excluded** from version control because it contains a private key that
grants full administrative access to the Firebase project (bypassing all security rules).
Committing such a key — even to a private repo — is a permanent leak.

If you need the service account key on a server or in a build/deploy pipeline, provide it
out-of-band, for example:

- Store it as an environment variable / secret manager entry
  (`GOOGLE_APPLICATION_CREDENTIALS` pointing at a path outside the repo), or
- Place it directly on the target server outside the git working tree.

The `.gitignore` in this repo blocks common service-account and secret filename patterns
so a key is not committed by accident.

> If this key has already been shared or committed anywhere, rotate it in the
> Google Cloud / Firebase console (IAM → Service Accounts → Keys).
