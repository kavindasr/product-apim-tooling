## apictl delete api-product

Delete API Product

### Synopsis

Delete an API Product from an environment

```
apictl delete api-product (--name <name-of-the-api-product> --version <version-of-the-api-product> --provider <provider-of-the-api-product> --environment <environment-from-which-the-api-product-should-be-deleted>) [flags]
```

### Examples

```
apictl delete api-product -n LeasingAPIProduct -v 1.0.0 -r admin -e dev
apictl delete api-product -n CreditAPIProduct -v 1.0.0 -e production
NOTE: Both the flags (--name (-n), --version (-v), and --environment (-e)) are mandatory.
```

### Options

```
  -e, --environment string   Environment from which the API Product should be deleted
  -h, --help                 help for api-product
  -n, --name string          Name of the API Product to be deleted
  -r, --provider string      Provider of the API Product to be deleted
  -v, --version string       Version of the API Product to be deleted
```

### Options inherited from parent commands

```
  -k, --insecure   Allow connections to SSL endpoints without certs
      --verbose    Enable verbose mode
```

### SEE ALSO

* [apictl delete](apictl_delete.md)	 - Delete an API/MCPServer/APIProduct/Application in an environment

