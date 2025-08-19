## apictl undeploy

Undeploy an API/MCP Server/API Product revision from a gateway environment

### Synopsis

Undeploy an API/MCP Server/API Product revision available in the environment specified by flag (--environment, -e) from the gateway specified by flag (--gateway, -g)

```
apictl undeploy [flags]
```

### Examples

```
apictl undeploy api -n TwitterAPI -v 1.0.0 -r admin --rev 1 -g Label1 -g Label2 -e dev
apictl undeploy api -n PizzaAPI -v 1.0.0 --rev 2 --all-gateways -e dev
apictl undeploy mcp-server -n WeatherMCPServer -v 1.0.0 --rev 1 -g Label1 -g Label2 -e dev
apictl undeploy api-product -n LeasingAPIProduct -v 1.0.0 --rev 3 -g Label1 -e dev
```

### Options

```
  -h, --help   help for undeploy
```

### Options inherited from parent commands

```
  -k, --insecure   Allow connections to SSL endpoints without certs
      --verbose    Enable verbose mode
```

### SEE ALSO

* [apictl](apictl.md)	 - CLI for Importing and Exporting APIs and Applications and Managing WSO2 Micro Integrator
* [apictl undeploy api](apictl_undeploy_api.md)	 - Undeploy API
* [apictl undeploy api-product](apictl_undeploy_api-product.md)	 - Undeploy API Product
* [apictl undeploy mcp-server](apictl_undeploy_mcp-server.md)	 - Undeploy MCP Server

