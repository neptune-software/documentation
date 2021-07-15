# Documentation PoC


## Hosting

* The static site is hosted using [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/)

## Deploy Process

* We have an example `index.html` file in the root of this repo.
* On each push to master the GitHub Action Workflow [Publish](https://github.com/neptune-software/documentation/actions/workflows/publish.yml) will trigger.
    * The definition of that workflow can be found [here](https://github.com/neptune-software/documentation/blob/master/.github/workflows/publish.yml)
    * You can find the docs on how to publish [here](https://aka.ms/swaworkflowconfig).
    * Notice the `app_location` key, which sets your "working directory".
    * The `app_build_command` key specifies to run `./build.sh` which is an arbitrar example of a "build step". This step right now creates a folder `tempdir` and copies the `index.html` into it.
    * The `output_location` location expects the "final" build result of the static website, all contents of this folder will be uploaded to the static site.
* You are free to modify these, using the build steps/logic you deem necessesary.
    * e.g., the `build.sh` script is just an example of a build step.
* Once published, the final result is available on [docs.neptune-software.com](https://docs.neptune-software.com)

## Antora
* The HTML output of the static website is generated from the AsciiDoc sources using [Antora](https://docs.antora.org/antora/2.3/install/install-antora/).
* The [output directory](https://docs.antora.org/antora/2.3/playbook/output-dir/) must be set in the Antora playbook to match the above requirements.
* We should think about where to store the [Neptune UI for Antora](https://docs.antora.org/antora-ui-default/). 
