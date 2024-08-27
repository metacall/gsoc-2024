# GSoC'24 - BUILDER

Hey I'm Ashish aka [Ashpect](https://github.com/ashpect) and I had the oppurtunity to work on the project BUILDER for metacall under the Google Summer of Code Mentrship porogram.

You could find the project proposal doc [here](https://docs.google.com/document/d/1A4mXeMjOwjf9mdiE0yejHE5CYKSKUK1G6_K88jG9hWM/edit#heading=h.z6ne0og04bp5).

### Overview

The objective of this project is to **develop a command-line interface and library** for MetaCall, enabling **selective composition of Docker images for efficient deployment** in Docker and Kubernetes environments. This involves **leveraging the Buildkit API for robust image constructio**n, ensuring **rootless and daemonless operation** for compatibility, and **prioritizing sandboxing for security**. The aim is to support Function-as-a-Service development by generating compact images with r**educed dependencies and attack surfaces** and making **light weight images**, facilitating streamlined deployment workflows.

### How to use -

Please refer to the [README](https://github.com/metacall/builder) of the builder repository for detailed instructions on how to use the builder.

### Work Done -

- [x] **Buildkit** - Leveraging the Buildkit API for robust image construction
- [x] **Selective Composition** - Selective composition of Docker images for efficient deployment
- [x] **CLI** - A command-line interface for the builder.
- [x] **Library/Pkg** - A library for the builder/to build upon in future
- [x] **Rootless** - Running the builder in rootless mode to support in k8s
- [x] **Caching** - Caching for the builder to speed up the build process
- [x] **Testing** - Extensive testing of the builder. (Most of the tests are written, some are pending to be written)
- [] **Documentation** - Proper documentation for the builder (Documentation is done enough for setting up the project and running it from a dev point of view, but would like to do in detail as well as make it more user friendly)

Apart from this, some bugs identified in core were reported and fixed, for example : [here](https://github.com/metacall/core/pull/520) and [here](https://github.com/metacall/core/issues/515)

### Future Work -
- [] **Tests for all languages**, the current implementation should work for composing all languages spported by metacall theoretically, but extending tests to all languages to identify bugs is required. Currently, the gh actions tests are successfully tested and implemented for nodejs, python, and ruby.
- [] **Optimizations** - There are some small bugs and improvements that can be done in the builder, for which I have opened good first issues to encourage newcoers to try their hands on. I'll be guiding them throughout, and if urgency requires in the future, I will fix those myself.
- [] **Documentation** - Proper documentation for the builder, which is currently in progress.


Most of the work is in [metacall/builder](https://github.com/metacall/builder), so please check the repo out for more details. Also take a look at the metacall website [here](https://metacall.io) and the medium page [here](https://medium.com/@metacall) to understand more about metacall.