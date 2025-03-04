# Releases

## 1.40.0 (1/15/2022)

### New Features

- Base image metadata for xray
- Basic support for multiple image build engines (`--image-build-engine`, `--image-build-arch` parameters)

### Improvements

- dockerfile reverse engineering updates
- buildkit dockerfile instruction support
- name change

### Bug Fixes

- todo: add info

## 1.39.1 (11/12/2022)

## 1.39.0 (10/24/2022)

## 1.38.0 (8/27/2022)

### New Features

- Experimental 'debug' command
- JSON console output format

### Improvements

- refactored http-probe-exec and http-probe-exec-file to be host-exec and host-exec-file (breaking change)

### Bug Fixes

- todo: add info

## 1.37.6 (4/22/2022)

### Improvements

- Source image label in minified images
- Full image path enhancements for container entry info

### Bug Fixes

- Traced application signal handling bugfix
- Healthcheck instruction parsing bugfix

## 1.37.5 (3/20/2022)

### New Features

- Experimental Node.js package include flag
- Experimental Next.js(React.js) app include flags
- Experimental Nuxt.js(Vue.js) app include flags
- Ability to disable the ptrace data source

## 1.37.4 (2/27/2022)

### New Features

- Container probe feature to use one of the compose services to test/probe the target container (`--container-probe-compose-svc` flag and `container.probe` continue-after mode)
- Ability to override the container image name and/or tag when targetting a compose service (`--target-compose-svc-image` flag)
- Ability to wait before executing the HTTP probes (`--http-probe-start-wait` flag)
- Ability to wait before starting each compose service (`--compose-svc-start-wait` flag)
- Basic FastCGI protocol support in HTTP probes (docs TBD)
- New `registry` command and a basic `pull` subcommand
- `--include-new` build flag to keep new files created by target during dynamic analysis
- Supprot for stored global param in `slim.config.json`


### Improvements

- Improved containerized CI/CD environments support (`sensor-ipc-mode` and `sensor-ipc-endpoint` flags for `build` and `profile`)
- Docker host detection improvements
- Target container IP detection improvements
- Not minifying onbuild base images by default
- Not minifying already minified images
- Cleanup container resources on exit
- `include-cert-all` build flag enabled by default
- Propagate logging flags to sensor
- Not using default http probe if custom probes are already defined
- Many compose related enhancements (volume lookup enhancements, compose image detection and error handling, etc)
- Various monitoring engine enhancements
- Migrate from urfave/cli/v1 to urfave/cli/v2
- Dockerfile reverse engineering enhancements (HEALTHCHECK instruction support, improved RUN instruction reversing when ARGs are also used)

## 1.37.3 (12/10/2021)

### New Features

- Install command / docker cli plugin install option (preview version)

### Improvements

- Container and compose link handling enhancements
- Volume mounting enhancements
- Static analysis improvements
- Symlink handling improvements for builds
- Collecting file check filesystem activity
- Entrypoint/cmd override handling improvements

### Bug Fixes

- Volume mounting bug fixes for compose

## 1.37.1/1.37.2 (11/7/2021)

### New Features

- Ability to pull images from private registries (`--registry-account`, `--registry-secret`, `--docker-config-path` flags)

### Improvements

- Additional flags for compose (`dep-include-target-compose-svc-deps`, `compose-env-nohost`, `compose-env-file`, `compose-workdir`, `compose-project-name`)
- Variable substitution support in compose
- Detect duplicates by default in xray
- Resource cleanup when the build command exits
- `delete-generated-fat-image` flag to cleanup the non-optimized images when `docker-slim` builds images from source/Dockerfile
- Improved `maintainer` info collection for xray

### Bug Fixes

- Volume mounting bug fixes for compose

## 1.37.0 (9/23/2021)

### New Features

- Experimental docker-compose support for the build command
- Include cert flags to make it easier to keep certificate data in the optimized images

### Improvements

- Install script

## 1.36.4

## 1.36.3 (8/30/2021)

## 1.36.2 (8/5/2021)

## 1.36.1 (6/20/2021)

### Improvements

- `--cro-host-config-file`, `--cro-sysctl` and `--cro-shm-size` flags.
- M1 builds.

### Bug Fixes

- xray and sensor volume detection bug fixes.

### Improvements

- Ability to detect additional shells.
- Saving command report to /tmp directory if it's not possible to save it in the current working directory.
- Printing tag information for build command.

### Bug Fixes

- Default `continue-after` value handling fix (remove `probe` mode if http probing is disabled).
- Sensor not exiting when it's trying to copy a directory it already copied.

## 1.36.0 (6/12/2021)

### New Features

- Ability to find duplicate files for xray (`--detect-duplicates`, `--show-duplicates`).
- Ability to find all utf8 encoded files for xray using the `--detect-utf8` flag  (optionally dumping them to console, directory or tar file).
- Ability to find the files with special permissions (`--show-special-perms`).
- Ability to find all installed shells for xray.
- Container entry information for xray with file detection.
- Inherited image instructions (aka ONBUILD instructions) for xray.
- More image level stats for xray.

### Improvements

- Multiple tags for the build command.
- `--http-probe-off` flag for the build command to provide a shortcut to disable HTTP probing.
- Flexible target image handling to use non-default tags if the `latest` tag doesn't exist and no explicit tag is provided.

## 1.35.2 (5/2/2021)

### New Features

- `change-match-layers-only` xray flag to print only the layers that contain the matches.

### Improvements

- xray enhancement: printing to console by default for pattern or data matches.

### Bug Fixes

- Various xray command bug fixes.

## 1.35.1 (4/27/2021)

### Improvements

- Ability to combine `probe` and `exec` `continue-after` modes

### Bug Fixes

- Various xray command bug fixes

## 1.35.0 (4/14/2021)

### New Features

- Console color output (on by default; disable with `no-color`)
- Loading http probe request data from separate files
- Ability to execute external probe commands (`--http-probe-exec` and `--http-probe-exec-file` flags)
- Ability to preserve original files in the target container discarding its test runtime data (`--preserve-path` and `--preserve-path-file`)
- Ability to pull container images if they don't exist locally yet (`--pull` and `--show-plogs`)
- File hashing for xray (`--hash-data`)
- Additional flags to control the xray command executions (`--top-changes-max`, `--reuse-saved-image`)
- Ability to match by file path, file data and file hash for xray (`--change-path value`, `--change-data value`, `--change-data-hash value`)

### Improvements

- Lots of additional container build flags (`--tag-fat`, `--cbo-add-host`, `--cbo-build-arg`, `--cbo-label`, `--cbo-target`, `--cbo-network`, `--cbo-cache-from`).
- Additional container runtime flags (`--cro-runtime`)
- `sigint` should kill the running container (#186)

### Bug Fixes

- Various xray image layer inspection bug fixes

## 1.34.0 (1/29/2021)

### New Features

- New `xray` flags to control what layer change data to include in the generated reports (`layer-changes-max`, `all-changes-max`, `add-changes-max`, `modify-changes-max`, `delete-changes-max`)

### Improvements

- `host` network flag handling enhancements.
- Returning non-zero exit codes on failures
- Additional image checks to catch missing ENTRYPOINT/CMD instructions

### Bug Fixes

- Fixed container image listing bug that broke the `--target` value suggestions in the interactive prompt mode.

## 1.33.0 (12/12/2020)

### New Features

- Ability to interact with the temporary containers using the `--exec` and `--exec-file` flags

### Improvements

- `npm` support enhancements (makes it possible to use `npm start` in Dockerfiles, which isn't recommended though)

### Bug Fixes

- Various bug fixes.

## 1.32.0 (8/23/2020)

### New Features

- Mapping container ports to specific host ports analyzing image at runtime (`--publish-port` and `--publish-exposed-ports` flags)

### Improvements

- `seccomp` security profile generation capability updates
- User namespace handling improvements (thanks to `@solarnz`)

## 1.31.0 (8/13/2020)

### New Features

- Experimental HTTP probe command generation based on the API descriptions from the Swagger and OpenAPI specs (`--http-probe-apispec` and `--http-probe-apispec-file` flags)
- Image metadata editing capabilities to add, remove and update the LABEL, VOLUME, EXPOSE, ENV and WORKDIR instructions (`--new-workdir`, `--new-expose`, `--new-label`, `--new-volume`, `--remove-volume`, `--remove-env`, `--remove-label`, `--remove-expose` and `--image-overrides` combined with `--expose`, `--workdir`, `--env`, `--volume`, `--label`, `--env`)

### Improvements

- Layer change details available in the `xray` command reports when the `--changes` flag is set.
- System and engine information in the command reports to improve debugging
- Ability to enable crawling for the HTTP probes specified using the `--http-probe-cmd` flag
- Improved HTTP probe crawler documentation

## 1.30.0 (7/27/2020)

### New Features

- `lint` command (initial Dockerfile linting capabilities with a basic set of checks)
- HTTP probe crawler (automatically probes additional endpoints referenced in the processed targets; see the `--http-probe-crawl` and related flags)

### Improvements

- ARM64 support (need more people to test!)
- `--http-probe-exit-on-failure` flag to exit execution when all HTTP probe calls fail
- `--include-bin-file` and `--include-exe-file` flags to make it easier to specify multiple binaries and executables loading them from files
- `xray` command report enhancements

## 1.29.0 (3/18/2020)

### New Features

- Interactive CLI prompt

### Improvements

- `xray` command output improvements
- Additional image data saved with the `xray` command reports (`--add-image-manifest` and `--add-image-config` flags)

## 1.28.1 (3/9/2020)

### Improvements

- New `xray` parameters to control how much to show when it's printing the layer details (`--changes value` and `--layer value`)
- Image history enhancements and more data saved in the xray command reports

## 1.28.0 (3/6/2020)

### New Features

- `xray` command enhancements to show the detailed container image information including its layers and their files and directories (initial version).

### Improvements

- The `--exclude-pattern` `build` parameter to filter/exclude the artifacts in the optimized container.

## 1.27.0 (2/28/2020)

### New Features

- Option to set permissions, user and group information for the artifacts included with the `--include-*` parameters.
- Option to overwrite the permissions and ownership info in the optimized image using the new `--path-perms` and `path-perms-file` parameters.

### Improvements

- Option to run the containerized application using user and group information from the USER instruction.
- Filter leftover PID files.
- UX enhancements for the containers created using Dockerfiles.
- Additional debugging information.

### Bug Fixes

- Support for special install directories on Linux (to prevent failures when `docker-slim` is trying to save its state).

## 1.26.1 (11/28/2019)

### Improvements

- Saving command execution report, by default (`slim.report.json`).
- CLI output UX enhancements.
- Docker connect info checks.

### Bug Fixes

- Version check fixes when running in containers.

## 1.26 (11/16/2019)

### New Features

- Run `docker-slim` in containers.
- New distribution option ([`dslim/docker-slim`](https://hub.docker.com/r/dslim/docker-slim) image available in Docker Hub).
- Archive `docker-slim` state into a separate Docker volume.

### Improvements

- Default to continuing `docker-slim` execution after the http probing step is done when http probing is enabled.
- Improved IPC.
- Improved seccomp and metadata artifact copy option.
- Improved execution report.

## 1.25.3 (8/4/2019)

### New Features

- Build minified images from `source` using the new `--from-dockerfile` build flag (see `README.md` for details).

### Improvements

- Custom HTTP POST probes support request bodies

## 1.25.2 (7/21/2019)

### New Features

- Enhanced build command reports with additional container image metadata (using the global `--report` flag)
- Ability to update the minified image Dockerfile instructions (using the --new-cmd, --new-entrypoint, --new-expose, --new-workdir, --new-env and --image-overrides flags)
- Dockerfile volume support

### Improvements

- HTTP probes by default (you will have to disable HTTP probes if you don't need them)
- Various UX enhancements to provide better CLI feedback and to avoid generating minified images that might not work

### Bug Fixes

- TTY bug fix caused by an external dependency (used to track update download progress)

## 1.25.0 (4/23/2019)

### New Features

- Experimental ARM32 support
- Easy way to keep a shell in your image (just pass `--include-shell` to the `build` command)
- Easy way to include additional executables (`--include-exe` flag) and binary objects (`--include-bin` flag), which will also include their binary dependencies, so you don't have to explicitly include them all yourself
- `update` command - now you can update `docker-slim` from `docker-slim`!
- Current version checks to know if the installed release is out of date

### Improvements

- Improvements to handle complex `--entrypoint` and `--cmd` parameters

## Previous Releases

- Better Mac OS X support - when you install `docker-slim` to /usr/local/bin or other special/non-shared directories docker-slim will detect it and use the /temp directory to save its artifacts and to mount its sensor
- HTTP Probing enhancements and new flags to control the probing process
- Better Nginx support
- Support for non-default users
- Improved symlink handling
- Better failure monitoring and reporting
- The `--include-path-file` option to make it easier to load extra files you want to keep in your image
- CentOS support
- Enhancements for ruby applications with extensions
- Save the docker-slim command results in a JSON file using the `--report` flag
- Better support for applications with dynamic libraries (e.g., python compiled with `--enable-shared`)
- Additional network related Docker parameters
- Extended version information
- Alpine image support
- Ability to override ENV variables analyzing target image
- Docker 1.12 support
- User selected location to store DockerSlim state (global `--state-path` parameter).
- Auto-generated seccomp profiles for Docker 1.10.
- Python 3 support
- Docker connect options
- HTTP probe commands
- Include extra directories and files in minified images
