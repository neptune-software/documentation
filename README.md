# Neptune DXP Open Edition documentation
The documentation for the Neptune DXP Open Edition is hosted here on Neptune GitHub. We use separate branches for authoring, reviewing and publishing the documentation.

## Branches and Git workflow

### Authoring 
Create a new temporary branch from **neptune-docs** when starting to work on the documentation. Give the branch a speaking name, for example, "tile-configuration". 

### Reviewing
- When the author is finished writing, they assign a reviewer to the branch. 
- When the review is finished, the reviewer creates a "pull request" to merge the changes back into the main branch.
- After the merge the temporary branch can be deleted.

### Publishing
- The **neptune-docs** branch contains the final documentation to be published. (We plan to rename this branch to **main** and make it the default branch.)
- Publishing to https://docs.neptune-software.com is done via a separate GitHub repository: https://github.com/neptune-software/dxp-documentation.
- Antora pulls the content directly from the Git branches, see [Repositories and Content Source Roots](https://docs.antora.org/antora/2.3/content-source-repositories/).

#### Configuration files for deploy process
- _.github/workflows/[publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)_: Settings for publishing as Azure Static Web App
- _[build.sh](https://github.com/neptune-software/documentation/blob/master/build.sh)_: Optional build steps

#### Antora-related files
- _antora/html-output_: Generated HTML output
- _antora/neptune-ui/ui-bundle.zip_: Customized UI bundle
- _antora/[antora-poc-playbook_neptune.yml](https://github.com/neptune-software/documentation/blob/master/antora/antora-poc-playbook_neptune.yml)_: Antora playbook file


## Antora 

### Resources
* [Install and Run Antora Quickstart](https://docs.antora.org/antora/2.3/install-and-run-quickstart/)
* [Antora Default UI](https://docs.antora.org/antora-ui-default/) 

## Deploy process

### Publishing
* Each push to the **master** branch triggers the GitHub Action Workflow [Publish](https://github.com/neptune-software/documentation/actions/workflows/publish.yml).
* All content from the `app_location` folder is uploaded to the [static Azure site](https://docs-poc.neptune-software.com).
* The publish workflow can also be triggered manually.

### Setup
* The GitHub workflow is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)
* For all configuration options see [Specific settings for Azure Static Web App](https://aka.ms/swaworkflowconfig).
* The `app_location` folder is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml). You can skip the building step and  [publish directly from this folder](https://docs.microsoft.com/en-us/azure/static-web-apps/github-actions-workflow#skip-building-front-end-app).

### Additional build steps
* The `app_build_command` key specifies to run `./build.sh` which is an example of a "build step". This step right now creates a folder `tempdir` and copies the example `index.html` from the root folder into it.
* You are free to modify these, using the build steps/logic you deem necessary.

## Hosting

* The static site is hosted using [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/).
* URL: [docs-poc.neptune-software.com](https://docs-poc.neptune-software.com).
