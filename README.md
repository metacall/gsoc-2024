[Google Summer of Code 2025](https://github.com/metacall/gsoc-2025)

# Google Summer of Code 2024
List of project ideas for contributors applying to the Google Summer of Code program in 2024 (GSoC 2024).

## Timeline/milestones

Please always refer to the [official timeline](https://developers.google.com/open-source/gsoc/timeline).  
  
## Application Process

#### 0. Get familiar with GSoC

First of all, and if you have not done that yet, read [the contributor guide](https://google.github.io/gsocguides/student/) which will allow you to understand all this process and how the program works overall. Refer to its left side menu to quick access sections that may interest you the most, although we recommend you to read everything.  
  
#### 1. Discuss the project idea with the mentor(s)

This is a required step unless you have dived in into the existing codebase and understood everything perfectly (very hard) and the idea you prefer is on the list below.

If your idea is not listed, please discuss it with the mentors in the available [contact channels](https://github.com/metacall/gsoc-2024#find-us). We're always open to new ideas and won't hesitate on choosing them if you demonstrate to be a good candidate!  
  
#### 2. Understand that

- You're committing to a project and we may ask you to publicly publish your weekly progress on it.
- We will repeatedly ask you to give feedback on our mentorship and management.
- You wholeheartedly agree with the [code of conduct](https://github.com/metacall/core/blob/develop/.github/CODE_OF_CONDUCT.md).
- You must tell us if there's any proposed idea that you don't think would fit the timeline or could be boring (yes, we're asking for feedback).
  
#### 3. Fill out the application form

We recommend you to follow [Google's guide to Writing a Proposal](https://google.github.io/gsocguides/student/writing-a-proposal) as we won't be too harsh on the format and we won't provide any template. But hey, we're giving you a starting point!

You can send the proposal link to any readable format you wish: Google Docs, plain text, in markdown... and preferably hosted online, accessible with a common browser **without downloading anything**.

We highly recommend you to ask for a review anytime to the community or mentor candidates before the contributor application deadline. It's much easier if you get feedback early than to wait for the last moment.
  

## Project Ideas

You can also propose your own.

### CLI / Deploy / FaaS Unification

**Skills**: Bash, Batch, PowerShell, JavaScript, TypeScript

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Medium

**Description**:

MetaCall offers binaries and a CLI that can be downloaded and installed easily through [`metacall/install`](https://github.com/metacall/install). This provides a CLI for executing code and a REPL for interacting with some MetaCall functionalities. A part from this, there is two separated projects that are part of the full development lifecycle, [`metacall/deploy`](https://github.com/metacall/deploy) which is a CLI for deploying into the [FaaS](https://dashboard.metacall.io) and [`metacall/faas`](https://github.com/metacall/faas) which is a reimplementation of the FaaS for local development. These two tools are right now completely separated from the CLI although they are necessary for the full development lifecycle. The idea of this project is to unify them into the same project. For example, having `metacall deploy ...` for executing the deploy CLI, or `metacall faas` for executing the FaaS locally. With this options, all tools will be unified into one and the end users will install all of them once the CLI is installed. For achieving this we are open to proposals but probably it will be needed to modify the install scripts (Unix and Windows) and install both projects as a post-install step and modify the launcher for recognizing these additional options for launching those tools.

**Expected outcomes**: Cross-platform implementation of unified install scripts for installing together the Deploy CLI and the FaaS with the main core CLI.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Gil Arasa Verge, Raj Aryan

**Resources**:
 - MetaCall Install: https://github.com/metacall/install
 - MetaCall Deploy: https://github.com/metacall/deploy
 - MetaCall FaaS: https://github.com/metacall/faas

### MacOS Distributable

**Skills**: C/C++ Dependency Management, CMake, Bash, DevOps

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Hard

**Description**:

MetaCall has multiple runtimes embedded on it and one of its objectives is to be as cross platform as possible. Each runtime has its own dependencies which create a huge dependency tree sometimes. This is a big complexity that is difficult to handle. Currently we are using Guix as our build system in Linux and we achieved to compile MetaCall and make it completely self-contained (in Linux for amd64 at the moment of writting). This allows MetaCall to be installed even in a BusyBox and work properly without any other system dependency. Current implementation of the build system consist of 3 repositories:

 - Distributable Linux: https://github.com/metacall/distributable-linux
 - Distributable Windows: https://github.com/metacall/distributable-windows
 - Distributable MacOs: https://github.com/metacall/distributable-macos

The objective of this idea is to improve the MacOS support:
 - Implementing the build script for MacOs with portable dependencies on the automated CI, in a similar way to how Windows distributable has been done.
 - Add tests in order to verify the MacOs portable installation.
 - Improve the install script for Linux [by adding support to MacOs](https://github.com/metacall/install/blob/0f145d4ee5a60b58f7c48f043ed7d0b7d6268609/install.sh#L210) so it can support both platforms at the same time, this will require testing with MacOs too, so another CI with MacOs as runner should be implemented in order to test it through the install script.

**Expected outcomes**: To implement and complete CI/CD builds for MacOS in order to provide cross-platform binary distributions of MetaCall with the maximum amount of languages possible. Extend the current install script for taking into account MacOs and provide testing environment for the MacOs distributable itself and the install script for MacOs.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Gil Arasa Verge

**Resources**:
 - MetaCall Core Windows Environment Install Script: https://github.com/metacall/core/blob/develop/tools/metacall-environment.ps1


### Connect Core CI with Distributables

**Skills**: GitHub Actions, Bash, Batch

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Medium

**Description**:

MetaCall provides binary distributions through an installer for end users. In order to provide binaries that follow latest versions with the main core repo, we would need to have those external distributable repositories linked to the releases of the main core repository. The objective of this project would be to design CIs that link all those repositories with the main core repository, so each time a new version is tagged in the main repository, all distributables are generated for the latest version. This will also help to check if there is a breaking change of the last version with the distributables. This may require to modify existing CIs and think about new ways of handling the contiuous delivery of the organization.

**Expected outcomes**: Consistent CI across multiple repositories in order to provide continouous delivery of MetaCall binaries with report of errors for when some distributable fails on a version of MetaCall Core.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Gil Arasa Verge

**Resources**:
 - MetaCall Core: https://github.com/metacall/core
 - MetaCall Windows Distributable: https://github.com/metacall/distributable-windows
 - MetaCall Linux Distributable: https://github.com/metacall/distributable-linux
 - MetaCall MacOS Distributable: https://github.com/metacall/distributable-macos

### MetaCall Core Sandboxing with CLI integration

**Skills**: C/C++, Linux Kernel

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Medium

**Description**:

Modern runtimes like Deno provide a command line interface for allowing / restricting capabilities and sandbox the execution of the code. We want to provide a similar approach but based on libseccomp. This approach will provide MetaCall CLI a standard system for filtering system calls independently of the language being executed. This will provide a safe sandboxing primitives that can be shared between runtimes at system call level. As a result MetaCall will be able to be executed safely without need to use Docker or any other virtualization tool.

MetaCall Core has a plugin extension system which allows to provide additional functionality to the core without the need of modifying the core itself. Right now one example of those plugins is the `backtrace`, it provides full stack trace in a cross-platform manner for when there is a segmentation fault. We want also to provide sandboxing in Linux for multiple architectures through the use of `libseccomp`. A part from this, we also want it to be fully configurable from the CLI. So for example, we can do somethin like: `metacall --disable-filesystem main.js` and if the `main.js` script tries to load a file from the filesystem, the kernel will kill the program.

**Expected outcomes**: A full sandboxed implementation that can be used either programatically or through CLI options.

**Possible mentors**: Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Vicente Eduardo Ferrer Garcia

**Resources**:
 - MetaCall Sandboxing Current State: https://github.com/metacall/core/pull/470
 - `libseccomp` GitHub Repository: https://github.com/seccomp/libseccomp
 - Example of usage for `libseccomp`: https://github.com/gebi/teach-seccomp/blob/master/step-2/example.c
 - Example of CMake find script for `libseccomp`: https://webkit-search.igalia.com/webkit/source/Source/cmake/FindLibseccomp.cmake
 - MetaCall CLI Source: https://github.com/metacall/core/tree/develop/source/cli/metacallcli
 - Deno Permission List: https://deno.land/manual/getting_started/permissions#permissions-list

### FaaS TypeScript Reimplementation

**Skills**: TypeScript

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:
This project offers a reimplementation of [MetaCall FaaS](https://dashboard.metacall.io) but with a simpler and less performant implementation. The objective of this FaaS reimplementation is to provide a simple and portable FaaS that can be run from the CLI in order to locally test the functions and complete projects that can be deployed into MetaCall FaaS. This is a very important part of the project because it is needed in order to fullfill the developer workflow when developing distributed polyglot applications.

It should mimick the [MetaCall FaaS REST API](https://github.com/metacall/deploy/blob/master/src/test/integration.protocol.spec.ts) but without need of authentication and with only the required capabilities for development. This repository will share parts with MetaCall FaaS through [MetaCall Protocol](https://github.com/metacall/protocol) so code can be reused between the repositories.

For better deployment, the MetaCall FaaS should be integrable with MetaCall CLI, providing a self contained distributable with all the compiled code which can be launched or invoked from an external CLI via API.

**Expected outcomes**: An embeddable library that can be used for locally testing MetaCall projects as if they were hosted on the FaaS.

**Possible mentors**: Thomas Rory Gummerson, Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Vicente Eduardo Ferrer Garcia, Raj Aryan

**Resources**:
 - MetaCall FaaS TypeScript reimplementation repository: https://github.com/metacall/faas
 - MetaCall FaaS: https://dashboard.metacall.io
 - Video Deploying a hundred functions into MetaCall FaaS using the Dashboard: https://www.youtube.com/watch?v=2RAqTmQAWEc
 - MetaCall Protocol: https://github.com/metacall/protocol
 - MetaCall Deploy: https://github.com/metacall/deploy

### MetaCall Examples CI

**Skills**: GitHub Actions, Bash, Devops

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

Currently there is no way to test all the examples and deployable examples of Metacall. The goal is to create a comprehensive CI system for all the examples of the core and Metacall FaaS, you would need to create a single repository for each Metacall version. Each repository would download the distributables for all supported operating systems, clone the example repositories from the Metacall's GitHub account, and run each example to test it. This would ensure that all examples are working correctly on all supported platforms for new releases.
Similarly, the same process would be followed for the [@metacall/deploy](https://github.com/metacall/deploy) package, where deployable examples would be cloned and deployed to a FaaS website using Deploy CLI to ensure that they are working as expected.

**Expected outcomes**:

The expected outcome will be a comprehensive testing and deployment system that ensures all examples for the Metacall and FaaS are working correctly on all supported platforms. This will provide confidence to users that the software is functioning as expected and will reduce the likelihood of issues arising in production. Additionally, this system could be used to automate future updates and releases, further streamlining the development process.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Gil Arasa Verge, Raj Aryan

**Resources**:
 - Distributable Linux: https://github.com/metacall/distributable-linux
 - Distributable Windows: https://github.com/metacall/distributable-windows
 - Distributable MacOs: https://github.com/metacall/distributable-macos
 - MetaCall Protocol: https://github.com/metacall/protocol
 - MetaCall Deploy: https://github.com/metacall/deploy
 - MetaCall FaaS: https://dashboard.metacall.io
 - Video Deploying a hundred functions into MetaCall FaaS using the Dashboard: https://www.youtube.com/watch?v=2RAqTmQAWEc

### Linux Distributable

**Skills**: C/C++ Depependency Management, CMake, Guix, Guile, Bash, Docker, BuildKit, DevOps

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Hard

**Description**:

At the moment of writing, Linux distributable is one of the best suited distributions that we have right now. But it is not completed and it has [some issues](https://github.com/metacall/distributable-linux/issues). The main objective of this project will be to solve those issues, either focused on the user experience or the development of other applications by means of using MetaCall Core embedded into them. Here's the list of the objectives:

 - Solve issues related to environment variables[[1]](https://github.com/metacall/distributable-linux/issues/5)[[2]](https://github.com/metacall/distributable-linux/issues/14), this will require generate an environment variable file based on `guix shell` and it will let us remove [the current approach used in the install script](https://github.com/metacall/install/blob/0f145d4ee5a60b58f7c48f043ed7d0b7d6268609/install.sh#L376).
 - Solve problems with [existing languages not working](https://github.com/metacall/distributable-linux/issues/1), and extend it in order to support more languages, including extending support for [additional features](https://github.com/metacall/distributable-linux/issues/11).
 - Improve support for embedders in order to have portable binaries that can be embedded easily into other languages like C/C++/Zig/Rust[[1]](https://github.com/metacall/distributable-linux/issues/15)[[2]](https://github.com/metacall/zig-example).
 - Adding [new architectures](https://www.gnu.org/savannah-checkouts/gnu/autoconf/manual/autoconf-2.70/html_node/Specifying-Target-Triplets.html#Specifying-Target-Triplets) to Linux with their respective tests (for this it is possible to use Docker multi-architecture for supporting those tests) and the install script support for those architectures.

**Expected outcomes**: A better and more stable version of MetaCall Linux Distributable which addresses the current errors and user experience problems.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Gil Arasa Verge

**Resources**:
 - Guix Shell: https://guix.gnu.org/manual/devel/en/html_node/Invoking-guix-shell.html
 - Guix Build System options: https://guix.gnu.org/manual/en/html_node/Additional-Build-Options.html
 - Docker Multi-Arch support: https://docs.docker.com/desktop/multi-arch/

### MetaCall Deploy Integrations

**Skills**: TypeScript, JavaScript

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

We have implemented support for [deployments through CLI](https://github.com/metacall/deploy) and now we require to integrate this CLI/Library into more environments in order to improve the development and adoption of MetaCall FaaS. For this there is a list of required tasks to do:
- Visual Studio Extension
- Github CI action
- OpenAPI integration

**Expected outcomes**: 

 - Create a Visual Studio Extension for one click deployment so you don't even need to use the command line for deploying MetaCall projects.
 - Create a GitHub action for integrating MetaCall deployments with your own CI if required.
 - Create a library for exporting the current MetaCall Inspect format into OpenAPI format, so it can be used easily on other projects.

**Possible mentors**: Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Raj Aryan

**Resources**:
  - Visual Code Extension: https://code.visualstudio.com/api/get-started/your-first-extension
  - GitHub Action: https://docs.github.com/en/actions/creating-actions/publishing-actions-in-github-marketplace

### Builder

**Skills**: Go, Docker, BuildKit, Sandboxing, Kubernetes

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:
Currently MetaCall is offered as Docker image on [Docker Hub](https://hub.docker.com/r/metacall/core). It includes 4 tags (`deps`, `dev`, `runtime` and `cli`) with only one architecture (`amd64`). Right now all the languages are packaged at once into the image, producing a big sized image, specially on the `dev` tag. The idea of this project is to implement a CLI with a separated API which provides a way to generate compact Docker images with MetaCall runtime. Docker does not allow to selectively choose from multiple layers merging them into one with efficient caching, we could do this by means of templating the Dockerfile itself but using the Buildkit API will make the solution much more robust and with the benefit of all the features from Buildkit like caching.

Another main requirement for this project is that it must be run under rootless and daemonless, inside a Dockerized environment (i.e this must be able to be run inside Docker without permissions and without a Docker daemon, so it can be run in a Kubernetes cluster, pushing and pulling the resulting images from a private registry).

This project has to be efficient and sandboxed, focused on FaaS development and producing compact images in terms of size and dependencies, so the bandwidth and attack surface is reduced.

**Expected outcomes**: A command line interface and library that is able to selectively compose docker images and run inside Docker/Kubernetes for MetaCall with efficient caching and compact size.

**Possible mentors**:  Fernando Vaño Garcia, Vicente Eduardo Ferrer Garcia, Gil Arasa Verge

**Resources**:
 - MetaCall Builder: https://github.com/metacall/builder

### Rust Actix + TypeScript React Server Side Rendering (tsx) Framework

**Skills**: Rust, TypeScript, React

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

For this project there are two approaches that can offer different user experiences but having in mind a similar result which is to develop TSX on top of Rust, or basically having an ergonomic and high performance server side rendering for TypeScript written in Rust. The two approaches are the following:

 1) Recently MetaCall has provided support for [inlining other languages into Rust](https://github.com/metacall/core/blob/adcc50496d53797011b87f42131cb857d0009ffb/source/ports/rs_port/tests/inline_test.rs#L13) through its macro system. This allows adding languages like Python or TypeScript into Rust easily. The main idea of this project is to create a Proof of Concept of an Actix server that easily embeds Server Side Rendering with TypeScript. This should be like a small framework which uses MetaCall and allows writing endpoint handlers where you can embed TypeScript directly with simplicity. In order to achieve this, the Rust Port will need to be extended, adding extra functionality required.
 2) If the first approach becomes problematic because Rust macros are limited for this *hacky* task, we may also provide an alternate and simpler approach which fullfills the objective. Basically we should provide a server that is able to load TSX lambdas and render them out of the box. Those lamdas would be written in a separate file a part from Rust, in a folder. A similar approach that [Granian HTTP Server](https://github.com/emmett-framework/granian) has followed but mainly focused on TSX Server Side Rendering.

Either using one or another approach, we should also support building static files and offer them with the Rust server, so we can have the complete lifecicle of development. For this we can embed [SWC](https://swc.rs/) which has great performance and it is written in Rust too.

The Proof of Concept should also contain benchmarks, in order to compare it to other server side rendering solutions or in order to be the baseline for future optimizations in MetaCall TypeScript support. Adding documentation and examples is needed too, so it can be reused in the future by other users and the functionality and utility of the framework is shown. Finally some complete examples should be provided so other users can learn by example how to use the framework and how to extend it. It does not require to have full support for production development but at least our objective is to have a minimal Proof of Concept that works.

**Expected outcomes**: A small framework based on Actix implementing server side rendering with React (TypeScript).

**Possible mentors**: Thomas Rory Gummerson, Jose Antonio Dominguez, Alexandre Gimenez Fernandez

**Resources**:
 - MetaCall Rust Port Crate: https://docs.rs/metacall/latest/metacall/
 - MetaCall Rust Port Source: https://github.com/metacall/core/tree/develop/source/ports/rs_port
 - MetaCall FaaS SSR Example: https://github.com/metacall/basic-react-SSR-example

## Find Us

The three chats are bridged by Matrix (messages sent from one, on the main room/channel, can be seen from all).

 - Telegram:
  <a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

 - Discord:
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

 - Matrix:
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>
