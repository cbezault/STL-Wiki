* Check for new versions of each of the components listed near the top of `azure-devops/provision-agent.ps1`.
* Test that the updated `azure-devops/provision-agent.ps1` correctly sets up all the new dependencies in a temporary Windows Server 2019 VM.
* Disable the other agents in Azure Pipelines and manually queue a build of `master` such that the temporary VM is used to build. This ensures that the new dependencies don't break the build.
* Create a pull request with the updated `azure-devops/provision-agent.ps1`, and merge that into `master`.
* Delete all the agents from Azure Pipelines on https://dev.azure.com/vclibs/STL/_settings/agentqueues?queueId=19&view=agents
* Recycle all the VMs in the virtual machine scale set "MSVCSTL-BUILD". They will automatically pick up the updated `provision-agent.ps1` and the new VMs will have updated dependencies installed.
* Create a pull request that updates the the `vcpkg` submodule and merge that to `master`.