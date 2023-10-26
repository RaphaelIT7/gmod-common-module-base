# gmod-common-module-base

This branch contains the actual [workflow](https://github.com/RaphaelIT7/gmod-common-module-base/blob/workflow/.github/workflows/compile.yml) which builds the project.

# Options
## Required Options
All options listed below are required to be added to your workflow.

#### PROJECT_NAME
> default: template

The Project to compile. This should be the same value as you set in the premake5.lua

## Project Options
All options listed below allow you to adjust the workflow to your needs.

#### PROJECT_PATH
> default: ""

The Path to the project

#### USE_PREFIX
> default: "true"

If enabled, it will use the gm[realm]_[Project]_[platform].[extension] format. Else, it will just use [Project].[extension] name.

#### REALM
> default: "sv"

The Realm this module is compiled for.

#### LINUX_FILEEXTENTION
> default: "dll"

The File extension for Linux compiles. Used in cases where you compile a .so file.

#### WINDOWS_FILEEXTENTION
> default: "dll"

The File extension for Windows compiles.

## Build Options
#### BUILD_64x
> default: "false"

If enabled, the Project is also compiled for the 64x

#### BUILD_32x
> default: "true"

If enabled, the Project is also compiled for the 32x

#### BUILD_WINDOWS
> default: "true"

If enabled, the Project is also compiled for Windows

#### BUILD_LINUX
> default: "true"

If enabled, the Project is also compiled for Linux

## Upload Options
#### ARTIFACT_EXPIRE
> default: 30

How long the Artifacts are available. 30 days by default.

#### PDB_ARTIFACT_EXPIRE
> default: 1

How long the Artifacts for .pdb files are available. 1 day by default.

#### UPLOAD
> default: "artifact"

How the result should be uploaded. Can be sftp or artifact. Only works for Linux.

#### UPLOAD_PATH
> default: "garrysmod/lua/bin/"

If UPLOAD is set to SFTP, it will upload the result in the given directory.

#### UPLOAD_PDB
> default: "false"

If enabled, the .pdb file will also be uploaded.

### SFTP Options
All options listed below are only used if `UPLOAD` is set to `sftp`.
SFTP wasn't tested much, so this could have some problems.

#### SFTP_IP
> default: ""

The IP of the SFTP server.

#### SFTP_PORT
> default: 22

The Port of the SFTP server.

#### SFTP_USER
> default: ""

The user for the SFTP server.

#### SFTP_PASSWORD
> default: ""

The password to use for the SFTP server.

#### SFTP_PRIVATE_KEY
The Private Key to use for the SFTP server. Leave this empty to use a password.

## Repository Options
This will list a bunch of options that allow you to use, for example a custom Garry'd Mod common repository or a custom SourceSDK.

#### GARRYSMOD_COOMON
> default: "danielga/garrysmod_common"

The garrysmod_common repository to use. Useful if you have a custom one you want to use.

#### GARRYSMOD_COOMON_BRANCH
> default: "master"

The garrysmod_common branch to use.

#### GARRYSMOD_COOMON_64XBRANCH
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
