# gmod-common-module-base
This is the module structure I use for my projects.

## Project Creation

First you want to set all project names in these files:  
- `premake5.lua`  
- `.github/workflow/compile.yml`  
- `development/module/premake5.lua`  

Then you can generate the project files by executing the `build.bat` thats inside the `development/module` folder.  
Now you can find the generated `.sln` file inside the `development/module/projects/windows/vs2022` folder.  


## Build Workflow
The [workflow](https://github.com/RaphaelIT7/gmod-common-module-base/tree/workflow) Branch contains a workflow that allows you to build your project with GitHub actions very easily.  
If you have any requests or issues with the workflow, feel free to open an issue for it.

Example of the workflow:
```yml
jobs:
  build:
    uses: RaphaelIT7/gmod-common-module-base/.github/workflows/compile.yml@workflow
    with:
      PROJECT_NAME: "template"
      BUILD_64x: "true"
```
