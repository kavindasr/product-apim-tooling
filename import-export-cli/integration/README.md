# APICTL Integration testing

## Pre-requisites for running integration tests
1. In order to run the integration tests, two instances of API Manager need to be started. By default integration tests are configured to run against local instances with port offset 0 and 1. If you need to configure the instances differently, it can be done as explained later on in the document. These two instances will act as the APIM environments that will be used for testing exporting and importing scenarios respectively. The integration tests will execute apictl commands, DCR calls, REST API calls and admin service calls against these instances.

2. Before starting the APIM instances update the APIM *deployment.toml* to allow the `@` character as part of the service provider name. This is to support DCR for tenant users since the `@` is part of the username. The updated config should look as follows,
(**If this test suite is running on a Windows machine, make sure to disable security scans and security guards of that machine prior to the test suite starts.)
```
[service_provider]
sp_name_regex = "^[@\\sa-zA-Z0-9._-]*$"
```

3. The `integration/config.yaml` contains the global configurations of the integration tests. It currently governs the following,

- *APIM Environment configs* 

  APIM environment instances mentioned previously. Default configuration is local instances with port offset **0** and **1** respectively as shown below. These must be changed to suite your APIM instances if they vary.

 ```
 environments:
- name: development
  host: localhost
  offset: 0
- name: production
  host: localhost
  offset: 1
```

- *solr indexing delay*

When artifacts such as APIs and API Products are created in APIM, solr indexes are updated to make these new artifacts searchable. A time delay needs to be allowed for this process to take place so that these artifacts will be successfully retrieved. This delay can be specified in _milliseconds_. Not providing a sufficient delay interval will lead to test failure because created artifact will not be returned when listed using the APIM REST API.

```
indexing-delay: 1000   
```


- *APIM DCR/REST API versions*

   The DCR and REST API versions (Admin, Devportal and Publisher) of the APIM instances mentioned previously.

```
dcr-version: v0.17
admin-rest-api-version: v3
devportal-rest-api-version: v2
publisher-rest-api-version: v3
devops-rest-api-version: v0
```

- *apictl version*

   The version of the apictl that is being integration tested.

```
apictl-version: 4.1.6
```   


4. Build the apictl source to create the archive distribution of your choice.
   > **Note:** Backup and delete API-CTL user directories (`~/.wso2apictl.local`, `~/.wso2apictl`)
   > if you already currently worked with different version of API-CTL.

## Executing command

| All commands must be run from *integration* directory

### Flags ###

- Required:

   `-archive` :  apictl archive file that is to be tested

- Optional:

   `-run` : Run specific test fucntion only

   `-v` : Print verbose test output, useful for debugging

   `-logtransport` : Print http transport level request/responses



### Command ###

> **Note:** If you wish to run integration tests in macOS, increase the maximum limits in macOS file descriptors with following command.
> Otherwise, you may experience the issue [1].
> ```sh
> ulimit -n 10032
> sudo launchctl limit maxfiles 65536 200000
> ```
> Ref: [2]

- Basic command

```
go test -p 1 -timeout 0 -archive <apictl archive name>

example: go test -p 1 -timeout 0 -archive apictl-4.1.6-linux-x64.tar.gz

```

- Run a specific test function only

```
go test -p 1 -timeout 0 -archive <apictl archive name> -run <Test function name or partial name regex>

example: go test -p 1 -timeout 0 -archive apictl-4.1.6-linux-x64.tar.gz -run TestVersion
```

- Print verbose output

```
go test -p 1 -timeout 0 -archive <apictl archive name> -v

example: go test -p 1 -timeout 0 -archive apictl-4.1.6-linux-x64.tar.gz -v
```

- Print http transport request/responses

```
go test -p 1 -timeout 0 -archive <apictl archive name> -logtransport

example: go test -p 1 -timeout 0 -archive apictl-4.1.6-linux-x64.tar.gz -logtransport
```

---
- [1] https://github.com/golang/go/issues/3575
- [2] https://wilsonmar.github.io/maximum-limits/
