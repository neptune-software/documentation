# Documentation PoC

## Hosting

* The static site is hosted using [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/).
* URL: [docs.neptune-software.com](https://docs.neptune-software.com).

## Deploy process

### Publishing
* On each push to the **master** branch the GitHub Action Workflow [Publish](https://github.com/neptune-software/documentation/actions/workflows/publish.yml) is triggered.
* All content from the `app_location` folder is uploaded to the static Azure site. The URL is [docs.neptune-software.com](https://docs.neptune-software.com).
  
### Setup 
* The GitHub workflow is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)
* For all configuration options see [Specific settings for Azure Static Web App](https://aka.ms/swaworkflowconfig).
* The `app_location` folder is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml). You can skip the building step and  [publish directly from this folder](https://docs.microsoft.com/en-us/azure/static-web-apps/github-actions-workflow#skip-building-front-end-app).
    
### Additional build steps
* The `app_build_command` key specifies to run `./build.sh` which is an example of a "build step". This step right now creates a folder `tempdir` and copies the example `index.html` from the root folder into it.
* You are free to modify these, using the build steps/logic you deem necessary.

## Antora
* The HTML output of the static website is generated from the AsciiDoc sources using [Antora](https://docs.antora.org/antora/2.3/install/install-antora/).
* We should think about where to store the [Neptune UI for Antora](https://docs.antora.org/antora-ui-default/). 
