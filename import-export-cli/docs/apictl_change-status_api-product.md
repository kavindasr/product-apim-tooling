## apictl change-status api-product

Change Status of an API Product

### Synopsis

Change the lifecycle status of an API Product in an environment

```
apictl change-status api-product (--action <action-of-the-api-product-state-change> --name <name-of-the-api-product> --version <version-of-the-api-product> --provider <provider-of-the-api-product> --environment <environment-from-which-the-api-product-state-should-be-changed>) [flags]
```

### Examples

```
apictl change-status api-product -a Publish -n TwitterAPI -v 1.0.0 -r admin -e dev
apictl change-status api-product -a Publish -n FacebookAPI -v 2.1.0 -e production
NOTE: The 3 flags (--action (-a), --name (-n), --version (-v) and --environment (-e)) are mandatory.
```

### Options

```
  -a, --action string        Action to be taken to change the status of the API Product
  -e, --environment string   Environment of which the API Product state should be changed
  -h, --help                 help for api-product
  -n, --name string          Name of the API Product to be state changed
  -r, --provider string      Provider of the API Product
  -v, --version string       Version of the API Product to be state changed
```

### Options inherited from parent commands

```
  -k, --insecure   Allow connections to SSL endpoints without certs
      --verbose    Enable verbose mode
```

### SEE ALSO

* [apictl change-status](apictl_change-status.md)	 - Change Status of an API, MCP Server or Product

