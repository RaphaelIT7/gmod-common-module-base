# gmod-common-module-base
This is the module structure I use for my projects.

## Build Workflow
The [workflow](https://github.com/RaphaelIT7/gmod-common-module-base/tree/workflow) Branch contains a workflow that allows you to build your project with GitHub actions very easily.  
If you have any requests or issues with the workflow, feel free to open an issue for it.

Example of the workflow:
```yml
jobs:
  build:
    uses: RaphaelIT7/gmodcommon-module-base/.github/workflows/compile.yml@workflow
    with:
      PROJECT_NAME: "template"
      BUILD_64x: "true"
```
