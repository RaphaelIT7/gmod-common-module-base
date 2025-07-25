# gmod-common-module-base

This branch contains the actual [workflow](https://github.com/RaphaelIT7/gmod-common-module-base/blob/workflow/.github/workflows/compile.yml) which builds the project.<br>
If you have any requests or issues with the workflow, feel free to open an issue for it.<br>

Example usage of this workflow:<br>
```yml
jobs:
  build:
    uses: RaphaelIT7/gmodcommon-module-base/.github/workflows/compile.yml@workflow
    with:
      PROJECT_NAME: "template"
      BUILD_64x: "true"
```

# Options
## Required Options
All options listed below are required to be added to your workflow.

#### PROJECT_NAME
> default: template

The project to compile. This should be the same value as you set in the premake5.lua

## Project Options
All options listed below allow you to adjust the workflow to your needs.

#### PROJECT_PATH
> default: ""

The Path to the project

#### USE_PREFIX
> default: "true"

If enabled, it will use the gm[realm]\_[Project]\_[platform].[extension] format. Else, it will just use the [Project].[extension] name.

#### REALM
> default: "sv"

The realm this module is compiled for.

#### LINUX_FILEEXTENTION
> default: "dll"

The file extension for Linux compiles. Used in cases where you compile a .so file.

#### WINDOWS_FILEEXTENTION
> default: "dll"

The file extension for Windows compiles.

## Build Options
#### BUILD_64x
> default: "false"

If enabled, the project is also compiled for the 64x

#### BUILD_32x
> default: "true"

If enabled, the project is also compiled for the 32x

#### BUILD_WINDOWS
> default: "true"

If enabled, the project is also compiled for Windows.

#### BUILD_LINUX
> default: "true"

If enabled, the project is also compiled for Linux.

#### BUILD_CACHE
> default: "false"

If enabled, the workflow will use ccache & GitHub's cache for project files to improve build speed.

## Upload Options
#### ARTIFACT_EXPIRE
> default: 30

How long the artifacts are available. 30 days by default.

#### PDB_ARTIFACT_EXPIRE
> default: 1

How long the artifacts for .pdb files are available. 1 day by default.

#### UPLOAD
> default: "artifact"

How the result should be uploaded. Can be `pterodactyl` or `artifact`. Only works for Linux/Windows always uses artifacts

#### UPLOAD_PDB
> default: "false"

If enabled, the .pdb file will also be uploaded.

## Pterodactyl Options

#### PTERODACTYL_PATH
> default: "garrysmod%2Flua%2Fbin%2f"

The path to upload the file into. Replace / with %2F

#### PTERODACTYL_RESTART
> default: "true"

If true, it will shutdown the server before uploading the file and afterwards start it back up.

#### PTERODACTYL_RESTART_SLEEPTIME
> default: "3"

How long it will sleep before uploading the new file, giving it time to properly shutdown.

### Secrets input

#### PTERODACTYL_KEY
> required: "false"

A client pterodactyl API key to use for uploading.

#### PTERODACTYL_SERVER
> required: "false"

The short server id, like `8b67a259` that the file will be uploaded onto.

#### PTERODACTYL_URL
> required: "false"

The url of the panel, like `localhost.com`. Don't include https:// or a slash after the url.

## Repository Options
This will list a bunch of options that allow you to use, for example a custom Garry'd Mod common repository or a custom SourceSDK.

#### GARRYSMOD_COMMON
> default: "danielga/garrysmod_common"

The garrysmod_common repository to use. Useful if you have a custom one you want to use.

#### GARRYSMOD_COMMON_BRANCH
> default: "master"

The garrysmod_common branch to use.

#### GARRYSMOD_COMMON_64XBRANCH
> default: "x86-64-support-sourcesdk"

#### SOURCESDK_MINIMAL
> default: "danielga/sourcesdk-minimal"

The sourcesdk-minimal repository to use. Useful if you have a custom one you want to use.

#### SOURCESDK_MINIMAL_BRANCH
> default: "master"

The sourcesdk-minimal branch to use.

#### SOURCESDK_MINIMAL_64XBRANCH
> default: "x86-64-branch"

The sourcesdk-minimal branch to use for the 64x compiles.

#### SCANNING
> default: "danielga/scanning"

The scanning repository to use.

#### SCANNING_BRANCH
> default: "master"

The scanning branch to use.

#### DETOURING
> default: "danielga/detouring"

The detouring repository to use.

#### DETOURING_BRANCH
> default: "master"

The detouring branch to use.

# Release Workflow
The release workflow has a few additional fields.<br>
For this workflow to work, you cannot set `UPLOAD`.<br>
[This is a template](https://github.com/RaphaelIT7/gmod-common-module-base/blob/workflow/.github/workflows/compile-release-template.yml)

#### RELEASE_PRE
> default: false

Marks the release as a pre-release

#### RELEASE_DRAFT
> default: false

Marks the release as a draft

#### RELEASE_LATEST
> default: false

Marks the release as the latest release

#### RELEASE_DELETEARTIFACT
> default: true

Deletes the uploaded artifacts from the workflow after they were added to the release.

#### RELEASE_PDB
> default: false

Adds the .pdb files to the release.<br>
NOTE: You also need to set `UPLOAD_PDB: "true"`