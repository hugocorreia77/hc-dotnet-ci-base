# hc-dotnet-ci-base

Base Docker image for .NET CI/CD pipelines using GitHub Actions.  
This image provides the .NET SDK (8 and 9) along with common dependencies used in build and test workflows.

---

## 📦 Available Images

Images are published automatically to [GitHub Container Registry (GHCR)](https://ghcr.io).

- `ghcr.io/hugocorreia77/hc-dotnet-ci-base:8` → Latest .NET 8 SDK
- `ghcr.io/hugocorreia77/hc-dotnet-ci-base:9` → Latest .NET 9 SDK
- `ghcr.io/hugocorreia77/hc-dotnet-ci-base:latest` → Alias for the latest supported version (currently .NET 9)

---

## 🛠 Installed Tools

Besides the .NET SDK, the image also includes:

- `git`
- `curl`
- `unzip`

A non-root user (`runner`) is also created for safer CI/CD execution.

---

## 🚀 Usage in GitHub Actions

You can use this base image in your workflows by referencing it in the `container` option:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container:
      image: ghcr.io/hugocorreia77/hc-dotnet-ci-base:9

    steps:
      - uses: actions/checkout@v4

      - name: Restore
        run: dotnet restore

      - name: Build
        run: dotnet build --configuration Release

      - name: Test
        run: dotnet test --no-build --verbosity normal
```

## 🔒 Security

All builds are scanned with Trivy to detect known vulnerabilities.
Only images that pass security checks are pushed to GHCR.
