## Proof of Concept

The complete PoC is hosted on Neptune GitHub; URL: <https://github.com/neptune-software/documentation>.

### Branches
The components of the PoC are stored in separate branches.

#### master
Configuration files for automated publishing process:
- _.github/workflows/publish.yml_: Settings for publishing as Azure Static Web App
- _build.sh_: Optional build steps

Antora-related files:
- _antora/html-output_: Generated HTML output
- _antora/neptune-ui/ui-bundle.zip_: UI bundle
- _antora/antora-poc-playbook_neptune.yml_: Antora playbook file

#### poc/v1.0 and poc/v2.0
Sample documentation source files in AsciiDoc for two versions of the Neptune DXP documentation and the style guide.

<https://docs.antora.org/antora/2.3/content-source-repositories/>

#### poc/neptune-ui
Source files for the Antora Neptune UI.

