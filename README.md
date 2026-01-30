# component-containerapps

Abstraction for resources needed when using Azure container apps. 

This repo delivers a set of components to abstract the details related to:
- Creating a docker image and pushing it to Azure container registry
- Deploy Azure Container app using the docker image. 
- Do both the image build and deployment as a single component.

# Usage
## Specify Package in `Pulumi.yaml`

Add the following to your `Pulumi.yaml` file:
Note: If no version is specified, the latest version will be used.

```
packages:
  containerapps: https://github.com/pulumi-pequod/component-containerapps[@vX.Y.Z]
``` 

## Use SDK in Program

### Python
```
from pulumi_pequod_containerapps import AppBuildDeploy, AppBuildDeployArgs

app_deployment = AppBuildDeploy(f"app-image", AppImageArgs(  
  resource_group_name = rg.name,
  app_path ="./app"
))
```

### Typescript
```
import { AppBuildDeploy } from "@pulumi-pequod/containerapps";

const appDeployment = new AppImageDeploy(baseName, {
  resourceGroupName: rg.name,
  appPath: "./app"
})
```

### Dotnet
```
using PulumiPequod.Containerapps;

var app = new AppBuildDeploy("app", new AppBuildDeployArgs 
{
    ResourceGroupName = resourceGroup.Name,
    AppPath = "./app",
    Platform = platform,
});
```

### YAML
```
  app:
    type: containerapps:AppBuildDeploy
    properties:
      resourceGroupName: ${resourceGroup.name}
      appPath: ./app
      platform: ${platform}
```



