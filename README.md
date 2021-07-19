# com.unity.ide.vscode fork

## Introduction

This fork has been created for use in Unity projects, where the actual Unity folder is a subfolder of the root folder, where the root folder may contain more tools and stuff like that.
In the case where there are other msbuild subprojects in the project root, in my case a few `csproj` files of the code generator project, a master solution needs to be generated that would reference all of these subprojects, for Intellisense to work correctly for any code in the repository.

Unity automatically includes this package in all new projects, pulling it from the official repo.
The repo is considered immutable any local changes being overwritten by the official image, and the code is stored only in cache, and so should not be exposed to source control.

A solution is to recreate the package locally, pointing Unity to this local folder instead of the official repo.
See [this reddit thread](https://www.reddit.com/r/Unity3D/comments/hmbm46/can_i_edit_a_unity_package/?utm_source=amp&utm_medium=&utm_content=post_body) for a rundown of a similar situation and the solution.


## How to import?

I've refactored the actual package to be a git submodule, so you can just include it as such into `Packages`.

```
git submodule add https://github.com/AntonC9018/com.unity.ide.vscode UNITY_PROJECT_SUBFOLDER/Packages/com.unity.ide.vscode
```

Unity will handle the rest of the process, modifying your `package-lock.json` accordingly.

Alternatively, you may store the dev repository in a different folder, and point `manifest.json` to that folder, as described in the reddit thread.
