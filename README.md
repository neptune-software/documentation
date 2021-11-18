# Neptune DXP Open Edition documentation
The documentation for the Neptune DXP Open Edition is hosted here on Neptune GitHub. We use separate branches for authoring and publishing the documentation. The current documentation is hosted here: [docs-poc.neptune-software.com](https://docs-poc.neptune-software.com).

## Workflow

The workflow is explained in detail in OneNote [here](https://parson01.sharepoint.com/sites/NeptuneDocumentationSupport/Freigegebene%20Dokumente/General/Notes%20for%20Neptune/).

The following gives a short summary:

### Authoring 
Create a new temporary feature branch from **main** when starting to work on the documentation. Give the branch a speaking name, for example, "tile-configuration". 

### Reviewing
* When the author finished writing, he creates a pull request in GitHub.
* In the pull request, he assigns one or more reviewer.
* When the review is done, the feature branch is merged back in the **main**.
* After the merge the temporary branch can be deleted.

### Publishing
* The **main** branch contains the final documentation to be published.
* Publishing to https://docs.neptune-software.com, where the documentation that is published on the Neptune website is located, is done via a separate GitHub repository: https://github.com/neptune-software/dxp-documentation.
* Antora pulls the content directly from the Git branches, see [Repositories and Content Source Roots](https://docs.antora.org/antora/2.3/content-source-repositories/).
* Each push to the **main** branch triggers the GitHub Action Workflow [Publish](https://github.com/neptune-software/documentation/actions/workflows/publish.yml).
* All content from the `app_location` folder is uploaded to the [static Azure site](https://docs-poc.neptune-software.com).
* The publish workflow can also be triggered manually.

#### Configuration files for deploy process
* _.github/workflows/[publish.yml](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)_: Settings for publishing as Azure Static Web App
* _[build.sh](https://github.com/neptune-software/documentation/blob/master/build.sh)_: Optional build steps

#### Antora-related files
* _antora/neptune-ui/ui-bundle.zip_: Customized UI bundle
* [_antora/neptune-docs-playbook_neptune.yml](https://github.com/neptune-software/documentation/blob/main/antora/neptune-docs-playbook.yml)_: Antora playbook file

#### Additional information
* The static site is hosted using [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/).
* For all configuration options see [Specific settings for Azure Static Web App](https://aka.ms/swaworkflowconfig).
* The `app_location` folder is defined in [publish.yml](https://github.com/neptune-software/documentation/blob/main/.github/workflows/publish.yml). You can skip the building step and  [publish directly from this folder](https://docs.microsoft.com/en-us/azure/static-web-apps/github-actions-workflow#skip-building-front-end-app).
* The `app_build_command` key specifies to run `./build.sh` which is an example of a "build step". This step right now creates a folder `tempdir` and copies the example `index.html` from the root folder into it. You are free to modify these, using the build steps/logic you deem necessary.


