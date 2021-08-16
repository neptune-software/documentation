# Proof of concept (PoC) for Neptune DXP documentation

## Hosting

* The static site is hosted using [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/).
* URL: [docs-poc.neptune-software.com](https://docs-poc.neptune-software.com).

## Deploy process

### Publishing
* Each push to the **master** branch triggers the GitHub Action Workflow [Publish](https://github.com/neptune-software/documentation/actions/workflows/publish.yml).
* All content from the `app_location` folder is uploaded to the [static Azure site](https://docs-poc.neptune-software.com).
  
### Setup 
* The GitHub workflow is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)
* For all configuration options see [Specific settings for Azure Static Web App](https://aka.ms/swaworkflowconfig).
* The `app_location` folder is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml). You can skip the building step and  [publish directly from this folder](https://docs.microsoft.com/en-us/azure/static-web-apps/github-actions-workflow#skip-building-front-end-app).
    
### Additional build steps
* The `app_build_command` key specifies to run `./build.sh` which is an example of a "build step". This step right now creates a folder `tempdir` and copies the example `index.html` from the root folder into it.
* You are free to modify these, using the build steps/logic you deem necessary.

## Branches
The complete PoC is hosted here on Neptune GitHub. The components of the PoC are stored in separate branches.
Antora pulls the content directly from the Git branches, see [Repositories and Content Source Roots](https://docs.antora.org/antora/2.3/content-source-repositories/).

### master

#### Configuration files for deploy process
- _.github/workflows/[publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)_: Settings for publishing as Azure Static Web App
- _[build.sh](https://github.com/neptune-software/documentation/blob/master/build.sh)_: Optional build steps

#### Antora-related files
- _antora/html-output_: Generated HTML output
- _antora/neptune-ui/ui-bundle.zip_: Customized UI bundle
- _antora/[antora-poc-playbook_neptune.yml](https://github.com/neptune-software/documentation/blob/master/antora/antora-poc-playbook_neptune.yml)_: Antora playbook file

### poc/v1.0 and poc/v2.0
* Sample documentation source files in AsciiDoc for two versions of the Neptune DXP documentation and the style guide.

### poc/neptune-ui
* Source files for the Antora Neptune UI.

## Antora 

### Resources
* [Install and Run Antora Quickstart](https://docs.antora.org/antora/2.3/install-and-run-quickstart/)
* [Antora Default UI](https://docs.antora.org/antora-ui-default/) 

### Build the PoC with Antora
Run the following command to generate the HTML output locally: 
`$ antora generate antora-poc-playbook_neptune.yml`