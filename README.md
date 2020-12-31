# VSTS

This role install the VSTS Build Agent on Windows or Linux servers.

## Requirements

There are no external requirements for this role.

## Role Variables

There are a few variables that can be set from the playbook if you like.

### download_dir

This is the directory where the VSTS installation package will be downloaded to.

#### Windows Default

```yaml
  download_dir: "C:\\Windows\\Temp"
```

#### Linux Default

```yaml
  download_dir: "/tmp"
```

### vsts_dir

This is the directory where VSTS will be extracted into

#### Windows Default

```yaml
  vsts_dir: "C:\\vsts"
```

#### Linux Default

```yaml
  terraform_dir: "/opt/vsts"
```

### vsts_version

This is the version of the VSTS agent that will be installed, the complete list can be found on the [Azure Pipelines Github Releases](https://github.com/Microsoft/azure-pipelines-agent/releases) page.

```yaml
  vsts_version: 2.175.2
```

## Unattended Required Variables

The following list of variables are used for installation of the agent, this role deploys a specific way currently, hopefuly as I progress more with Ansible this role will become more flexible. The complete list of options for [Windows](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops#required-options) or [Linux](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-linux?view=azure-devops#required-options).

### vsts_url

This is your Azure Devops Organization URL

```yaml
  vsts_url: https://dev.azure.com/myorganizationame
```

### vsts_auth

This variable defines the authentication option, we default to PAT

### vsts_token

This is the PAT token that is generated from within your Azure Devops Organization [see here](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page).

### vsts_pool

This is the name of the pool that your server will belong to [see here](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/pools-queues?view=azure-devops&tabs=yaml%2Cbrowser#creating-agent-pools).

### vsts_account

This is used for the Windows Installation, an admin account for the service to run as, currently this role does not create a user account.

### vsts_password

This is used for the Windows Installation, an admin account for the service to run as, currently this role does not create a user account.

## Dependencies

There are no external dependencies for this role.

## Example Playbook

This example shows the basic use of this role.

```yaml
    - hosts: all
      roles:
         - vsts
      vars:
        vsts_url: "https://dev.azure.com/myorganization"
        vsts_token: "PAT TOKEN"
        vsts_pool: "BuildAgents"
        vsts_account: "Administrator"
        vsts_password: "P@ssw0rd"
```

## License

MIT

## Author Information

My name is Jeff Patton, feel free to contact me via [issues](https://github.com/anisble-playbooks/vsts/issues).
