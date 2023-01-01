[![CI](https://github.com/tj-actions/docker-cp/workflows/CI/badge.svg)](https://github.com/tj-actions/docker-cp/actions?query=workflow%3ACI)
[![Update release version.](https://github.com/tj-actions/docker-cp/workflows/Update%20release%20version./badge.svg)](https://github.com/tj-actions/docker-cp/actions?query=workflow%3A%22Update+release+version.%22)
[![Public workflows that use this action.](https://img.shields.io/endpoint?url=https%3A%2F%2Fused-by.vercel.app%2Fapi%2Fgithub-actions%2Fused-by%3Faction%3Dtj-actions%2Fdocker-cp%26badge%3Dtrue)](https://github.com/search?o=desc\&q=tj-actions+docker-cp+path%3A.github%2Fworkflows+language%3AYAML\&s=\&type=Code)

## docker-cp

GitHub action to run steps using docker

## Examples

### Using a locally built image

```yaml
...
    steps:
      - uses: actions/checkout@v2

      - name: Set up QEMU
        uses: docker/setup-qemu-action@v2.1.0

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2.2.1

      - name: Build
        uses: docker/build-push-action@v3
        with:
          context: .
          load: true
          push: false
          tags: user/app:latest
      
      - name: Run
        uses: tj-actions/docker-cp@v2
        with:
          image: user/app:latest
          args: |
            echo "Hello World"
```

### Using an image from a registry

```yaml
...
    steps:
      - uses: actions/checkout@v2
      
      - name: Run ubuntu from dockerhub
        uses: tj-actions/docker-cp@v2
        with:
          image: ubuntu:latest  # OR gcr.io/cloud-builders/gradle
          args: |
            echo "Hello World"
```

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|    INPUT    |  TYPE  | REQUIRED |  DEFAULT  |          DESCRIPTION          |
|-------------|--------|----------|-----------|-------------------------------|
|  container  | string |   true   |           |        Container name         |
| destination | string |   true   |           | Destination file or directory |
|    local    | string |  false   | `"false"` | Copy from local to container  |
|   options   | string |  false   |           |      Additional options       |
|   source    | string |   true   |           |   Source file or directory    |

<!-- AUTO-DOC-INPUT:END -->

*   Free software: [MIT license](LICENSE)

If you feel generous and want to show some extra appreciation:

[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

[buymeacoffee]: https://www.buymeacoffee.com/jackton1

[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png

## Credits

This package was created with [Cookiecutter](https://github.com/cookiecutter/cookiecutter) using [cookiecutter-action](https://github.com/tj-actions/cookiecutter-action)

## Report Bugs

Report bugs at https://github.com/tj-actions/docker-cp/issues.

If you are reporting a bug, please include:

*   Your operating system name and version.
*   Any details about your workflow that might be helpful in troubleshooting.
*   Detailed steps to reproduce the bug.
