# com.unity.ide.vscode fork

## Introduction

This fork has been created for use in Unity projects, where the actual Unity folder is a subfolder of the root folder, where the root folder may contain more tools and stuff like that.
In the case where there are other msbuild subprojects in the project root, in my case a few `csproj` files of the code generator project, a master solution needs to be generated that would reference all of these subprojects, for Intellisense to work correctly for any code in the repository.

Unity automatically includes this package in all new projects, pulling it from the official repo.
The repo is considered immutable any local changes being overwritten by the official image, and the code is stored only in cache, and so should not be exposed to source control.

A solution is to recreate the package locally, pointing Unity to this local folder instead of the official repo.
See [this reddit thread](https://www.reddit.com/r/Unity3D/comments/hmbm46/can_i_edit_a_unity_package/?utm_source=amp&utm_medium=&utm_content=post_body) for a rundown of a similar situation and the solution.

**Summing up here:**

1. Open `Packages/manifest.json`.
2. Change `"com.unity.ide.vscode": "THE_VERSION"` to `"com.unity.ide.vscode": "PATH_TO_PACKAGE"`. Local to *this repo*, the package is located in `Packages/com.unity.ide.vscode`.


## How to import?

