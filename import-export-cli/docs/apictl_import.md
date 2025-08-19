## apictl import

Import an API/MCP Server/API Product/Application to an environment

### Synopsis

Import an API to the environment specified by flag (--environment, -e)
Import an API Product to the environment specified by flag (--environment, -e)
Import an MCP Server to the environment specified by flag (--environment, -e)
Import an Application to the environment specified by flag (--environment, -e)

```
apictl import [flags]
```

### Examples

```
apictl import api -f qa/TwitterAPI.zip -e dev
apictl import mcp-server -f qa/WeatherMCPServer.zip -e dev
apictl import api-product -f qa/LeasingAPIProduct.zip -e dev
apictl import app -f qa/apps/sampleApp.zip -e dev
```

### Options

```
  -h, --help   help for import
```

### Options inherited from parent commands

```
  -k, --insecure   Allow connections to SSL endpoints without certs
      --verbose    Enable verbose mode
```

### SEE ALSO

* [apictl](apictl.md)	 - CLI for Importing and Exporting APIs and Applications and Managing WSO2 Micro Integrator
* [apictl import api](apictl_import_api.md)	 - Import API
* [apictl import api-product](apictl_import_api-product.md)	 - Import API Product
* [apictl import app](apictl_import_app.md)	 - Import App
* [apictl import mcp-server](apictl_import_mcp-server.md)	 - Import MCP Server
* [apictl import policy](apictl_import_policy.md)	 - Import a Policy

