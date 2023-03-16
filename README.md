# s3fs for `arm`

Built from https://github.com/[maresb/docker-build-s3fs](https://github.com/maresb/docker-build-s3fs).

They provide a downloadable `.deb` binary for `s3fs` [here](https://github.com/maresb/docker-build-s3fs#download). However, it is only available for `amd` - Hence this repository, that leverages their docker image to publish an `arm` `s3fs` binary.

## Building and publishing a new version

To build and publish a new version for the `s3fs` binary, follow [the instructions from docker-build-s3fs](https://github.com/maresb/docker-build-s3fs#download). Note that you might need to use `docker buildx` instead of `docker build` to build the image for the target `arm` architecture.

After doing so, tag and push a new commit with the new version binary and respective checksum file:

```
git add s3fs_<version>_arm64.deb SHASUM_256
git commit -m "Add version $VERSION"
git tag $VERSION
git push
```

Then, publish a new release including both these files with a release title equal to the version (example release [here](https://github.com/adzerk/s3fs-arm/releases/tag/1.91)).
