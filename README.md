# go-devcontainer
The base devcontainer for Daytona Go projects

Basically this pulls out the devcontainer from `daytonaio/daytona` into its own repo and sets up a devcontainer prebuild GitHub action. This has a couple advantages.
1. Its prebuilt and a from scratch env goes from launching in ~5m to >1m (depending on network)
1. Its can be re-used across Daytona and all the plugins. So the resources usage for folks that develop plugins will drop since its shared.
1. Centralized also means common versions and only one place to update. Bumping go version for example.

You can use it with:
```
	"image": "ghcr.io/daytonaio/go-devcontainer:main"
```
Which will track the main branch of the repo. In the case that we want more stable environments. You can push a tag to the repo and it will automatically built a release version that can be used with (given the tag v0.0.1 as an example).
```
	"image": "ghcr.io/daytonaio/go-devcontainer:0.0.1"
    # or
    "image": "ghcr.io/daytonaio/go-devcontainer:0.0"
    # or 
    "image": "ghcr.io/daytonaio/go-devcontainer:0"
```

When you use `major` or `major.minor` as an image tag, these will be updated on subsequent tags. It will follow semver'ish versioning. 
* The safest is to pin to a specific `major.minor.patch`. 
* If you're ok with bugfixes you can pin to `major.minor`. 
* If don't mind changes so long as the the devcontainer interface (features, user, etc) doesn't change you can pin to `major`.