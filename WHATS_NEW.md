# Whats new

Latest changes for the RHOAS CLI.
For information on what was included in latest release please refer to our [changelog](https://github.com/redhat-developer/app-services-cli/blob/main/CHANGELOG.md)

## 0.50.0

### Support for Red Hat OpenShift Connectors
Our expanded support for Red Hat OpenShift Connectors is now available for you to use. You can create a Connector instance definition file by using `rhoas connector build`. A definition file can be used to create one or more Connector instances using `rhoas connector create`

`rhoas connector build` can be used to create a definition file for a Connector type.

`rhoas connector create` can be used to create a Connector instance based on the configuration you generated with `rhoas connector build`.

Use the `--type` flag to pick which connector type you want to deploy. You can list and search through all available Connector types use the command with the `--search` flag:
```bash 
rhoas connector type list --search=Amazon
```

Updating the state of a Connector instance can also be done from the CLI using the command:
```bash
rhoas connector update
```

You can also create a new namespace using the command:
```bash
rhoas connector namespace create
```

Each created Connector instances and namespaces are set in the active service context. To update your context or to remove services from the context for either a namespace or Connector instance use:
```bash
rhoas context unset --services=connector,namespace
``` 

## 0.49.0

### Support for Red Hat OpenShift Connectors
You are now able to interact with Red Hat OpenShift Connectors directly from the CLI. You can create a new connector by using `rhoas connector build` in conjunction with `rhoas connector create`.

Use the `--type` flag to pick which connector type you want to deploy. You can list and search through all availble connector types use the command with the `--search` flag:
```bash
rhoas connector type list
```

You can also create a new Connectors namespace using the command:
```bash
rhoas connector namespace create
```

Newly created Connectors instances and Connectors namespaces are set in the current service context. To update your context or to remove services from the context for either a namespace or connector use:
```bash
rhoas context unset --services=connector,namespace
``` 


## 0.48.0

### Support for configuration of Service Registry instances 
`rhoas service-registry setting get` for getting the value of a setting for a Service Registry instance. Supports the `--name` flag to define the setting name.

The setting name can also be prompted by running the command in interactive mode:
```
rhoas service-registry setting get
```

`rhoas service-registry setting set` for configuring the value of a setting for a Service Registry instance. Supports the `--name` flag to define the setting name and `--value` to define the setting value. `--default` restores the default value.

The setting name and value can also be prompted by running the command in interactive mode:
```
rhoas service-registry setting set
```

`rhoas service-registry setting list` for listing all settings for a Service Registry instance.

> NOTE: The `service-registry setting` command is only available to Service Registry instance owners, instance administrators, and organization administrators.


### Breaking changes for `rhoas generate-config` command

#### Deprecation of service account creation

Earlier versions of RHOAS CLI created service accounts and generated configuration file containing URLs to service instances and credentials for service accounts.

From this version, `rhoas generate-config` command will no longer create service accounts and the generated configuration file will only contain the URLs.

#### Support for ConfigMap output and deprecation of Secret output format

With config-generate command generating only URLs to the configuration file, it will be beneficial to have them generated in a ConfigMap format.

```
rhoas generate-config --type configmap
```

`rhoas generate-config` command no longer supports the secret output type. The credentials for service accounts can be generated in a Openshift secret file and can be used along with the ConfigMap for service instances.


## 0.46.0

### Support for Marketplace Billing model

`rhoas kafka create` now supports `--billing-model` flag that allow users to specify the type billing details for your kafka instance.

`--billing-model` along with `--marketplace` and `--marketplace-account-id` flags can be used to specify the
billing details.

Billing details can also be prompted by running the command in interactive mode:

```
rhoas kafka create
```

## 0.44.0 

### Support for consuming and producing to a topic

`rhoas kafka topic produce` and `rhoas kafka topic consume` for producing and consuming messages to a kafka topic.

New `produce` and `consume` commands work without any configuration and will point to your current Kafka instance by default.
Commands can act as alternative to kcat and kafka bin scripts by providing unified interface and simplicity of use.

> NOTE: commands are released as technology preview. Some of the flags and arguments can change without any notice.

### Generate Config

New `--overwrite` flag for `rhoas generate-config` enables users to overwrite their current configuration

## One SSO provider used by CLI

RHOAS CLI would use only single SSO provided by default. 
Users will not longer see multiple tabs opened when login and communicate with two different authentication servers.

> NOTE: This change should not affect users and it have been documented only for informational reasons

## Windows Powershell Suggestions

`rhoas completion powershell` will enable developers to get command completions on Windows platforms

> NOTE: Feature have been provided by our community. We are looking for feedback on usability of Powershell extensions.

### Support for Marketplace Billing model

`rhoas kafka create` supports now `--marketplace` and `--marketplace-account-id` flags that allow users to specify AWS marketplace details for billing purposes. 
