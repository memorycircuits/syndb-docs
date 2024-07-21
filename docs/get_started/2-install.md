# Installation
The SynDB platform provides several UIs directed towards different user groups. We recommend using the UIs for those getting started with SynDB. For advanced users, the API is the most flexible way to interact with the platform, see the [Advanced](#advanced) section.

## User interfaces
The SynDB interfaces are implemented with the Python programming language. To run them you need to have a Python environment.

!!! tip "Setup Python environment"
    This requires two things (1) Python interpreter installed in your system, (2) Python environment management for the SynDB packages.
    
    There many solutions to both requirements, we recommend using [`pyenv`](https://github.com/pyenv/pyenv-installer) to solve 1st problem, and [pipx](https://pipx.pypa.io/latest/installation) for the 2nd. Follow the installation guide for your operating system.

Install the SynDB CLI and GUI using the following commands:
=== "pipx"
    ``` bash
    pipx install syndb-cli[gui]
    ```
=== "pip"
    ``` bash
    pip install syndb-cli[gui]
    ```

### Upgrade
To upgrade the SynDB CLI along with the GUI (if installed), run the following command:
=== "pipx"
    ``` bash
    pipx upgrade syndb-cli
    ```
=== "pip"
    ``` bash
    pip install syndb-cli[gui] --upgrade
    ```

## Advanced

### `syndb-cli` without GUI
=== "pipx"
    ``` bash
    pipx install syndb-cli
    ```
=== "pip"
    ``` bash
    pip install syndb-cli
    ```

### Direct API usage
The API can be accessed through the [OpenAPI documentation]({{ api.url }}). For a more tailored approach, you may interact with the API through the `syndb-data` Python package:
=== "poetry"
    ``` bash
    poetry add syndb-data
    ```
=== "pip"
    ``` bash
    pip install syndb-data
    ```

Alternatively, you may generate your own language bindings using [`openapi-generator`](https://openapi-generator.tech/); you will need the [SynDB openapi schema]({{ api.openapi }}).
