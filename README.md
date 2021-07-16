# Documentation PoC

## Hosting

* The static site is hosted using [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/).
* The published website is available on [docs.neptune-software.com](https://docs.neptune-software.com).

## Deploy process

* On each push to the **master** branch the GitHub Action Workflow [Publish](https://github.com/neptune-software/documentation/actions/workflows/publish.yml) is triggered.
* All content from the `app_location` folder that is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml) is uploaded to the static Azure site.
* The GitHub workflow is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)
* [Specific settings for Azure Static Web App](https://aka.ms/swaworkflowconfig)
* Notice the `app_location` key, which sets your "working directory". You can [directly publish from this folder](https://docs.microsoft.com/en-us/azure/static-web-apps/github-actions-workflow#skip-building-front-end-app).
* We have an example `index.html` file in the root folder of this repo.
    
### Additional build steps
* The `app_build_command` key specifies to run `./build.sh` which is an arbitrary example of a "build step". This step right now creates a folder `tempdir` and copies the `index.html` from the root folder into it.
* You are free to modify these, using the build steps/logic you deem necessary. The `build.sh` script is just an example of a build step.

## Antora
* The HTML output of the static website is generated from the AsciiDoc sources using [Antora](https://docs.antora.org/antora/2.3/install/install-antora/).
* The [output directory](https://docs.antora.org/antora/2.3/playbook/output-dir/) must be set in the Antora playbook to match the above requirements.
* We should think about where to store the [Neptune UI for Antora](https://docs.antora.org/antora-ui-default/). 
