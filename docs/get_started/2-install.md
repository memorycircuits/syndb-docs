# Installation
The SynDB platform provides several UIs directed towards different user groups. We recommend using the UIs for those getting started with SynDB. For advanced users, the API is the most flexible way to interact with the platform, see the [Advanced](#advanced) section.

## User interfaces
The SynDB interfaces are implemented with the Python programming language. To run them you need to have a Python environment. We recommend using [pipx](https://pipx.pypa.io/latest/installation) to streamline the setup. Follow the installation guide for your operating system.

When pipx is ready, install the SynDB CLI and GUI using the following commands:

```bash
pipx install syndb-cli[gui]
```
**Advanced case**, you know that you won't use the GUI:
```bash
pipx install syndb-cli
```

## Advanced
SynDB provides access to its REST API for advanced users to access the data directly. The API can be accessed through the [OpenAPI documentation]({{ api.url }}). For a more tailored approach, you may interact with the API through the `syndb-data` Python package:

```bash
pip install syndb-data
```

Alternatively, you may generate your own language bindings using [`openapi-generator`](https://openapi-generator.tech/); you will need the most up-to date [SynDB openapi schema]({{ api.openapi }}).
