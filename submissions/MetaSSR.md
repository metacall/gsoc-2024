
# MetaSSR: A Server-Side Rendering Framework Built on Metacall and Rust

**Organization:** Metacall

**Contributor:** [Mohamed Emad](https://github.com/hulxv)

**Mentors:** Parra, A.G.

## Overview

MetaSSR is a Server-Side Rendering (SSR) framework that was built entirely from the ground up during the Google Summer of Code (GSoC) 2024 program. It serves as a real-world use case for the [Metacall](https://github.com/metacall/core) polyglot runtime, demonstrating how multiple programming languages can be utilized within a single SSR framework. Built with Rust and the [Axum](http://github.com/tokio-rs/axum) web framework, MetaSSR is designed to offer developers a high-performance, versatile tool for creating SSR web applications.

## Project Goals

The primary goals of the MetaSSR project were:

1. **Design and Build the Framework from Scratch:** Develop a new SSR framework from the ground up, focusing on seamless integration with Metacall and leveraging the strengths of Rust and Axum.

2. **Utilize Metacall and Polyglot Programming:** Showcase the power and flexibility of polyglot programming by enabling MetaSSR to support multiple languages within the same application, utilizing the Metacall runtime.

3. **Develop a Command-Line Interface (CLI):** Create an intuitive CLI tool to enable developers to easily create, build, and manage MetaSSR projects.

4. **Comprehensive Documentation:** Write detailed documentation to help users install, use, and contribute to MetaSSR, ensuring the framework is accessible to both new and experienced developers.


## Accomplishments

Throughout the GSoC period, I successfully achieved the following milestones:

### 1. Framework Design and Implementation

- **Core Framework Development:** Designed and implemented the core architecture of MetaSSR, with a focus on modularity and performance. Rust and Axum were chosen for their reliability and speed.
  
- **Metacall Integration:** Integrated Metacall from the beginning, allowing the framework to support polyglot programming, where components written in different languages can interact seamlessly within the same application.

### 2. Command-Line Interface (CLI)

- **CLI Tool Creation:** Developed a powerful CLI tool that allows developers to create, build, and run MetaSSR projects with simple commands.
  
- **User-Focused Design:** Ensured the CLI was easy to use, even for developers new to SSR frameworks or Rust.

### 3. Documentation

- **Installation and Usage Guides:** Authored comprehensive guides covering everything from installation to advanced usage scenarios, making it easy for developers to get started with MetaSSR.
  
- **Contributing Guidelines:** Created clear contributing and code of conduct files to encourage community involvement and maintain a positive, welcoming environment.

### 4. Community Engagement

- **Active Participation:** Regularly interacted with the Metacall community, sharing updates, soliciting feedback, and refining the framework based on real user needs.
  
- **Open-Source Contributions:** Contributed to other Metacall-related projects to help strengthen the ecosystem and ensure MetaSSR fits well within it.

## Challenges and Solutions

Building a new framework from scratch presented several challenges:

- **Architectural Decisions:** Choosing the right architecture for MetaSSR to ensure scalability and ease of use was critical. I addressed this by iterating on design concepts and seeking feedback from experienced developers.

- **Integration Complexity:** Ensuring smooth integration with Metacall while maintaining performance was challenging. I worked closely with Metacall contributors to optimize this integration.

- **Documentation Scope:** Crafting documentation that is both thorough and accessible to developers of all levels was a balancing act. I focused on clear explanations and practical examples to overcome this challenge.

## Impact

The development of MetaSSR from scratch has the potential to make a significant impact:

- **Innovative Polyglot Programming:** By allowing developers to use multiple languages within a single SSR framework, MetaSSR demonstrates the practical benefits of polyglot programming.
  
- **High Performance:** Built with Rust and Axum, MetaSSR is designed for speed and efficiency, making it suitable for production environments.
  
- **Community Growth:** As a new addition to the Metacall ecosystem, MetaSSR offers developers a fresh tool for building modern web applications, encouraging more contributions and engagement.


## Pull Requests and Contributions

During the GSoC season, and even before it officially began, I made several key contributions to the MetaSSR project and the broader Metacall ecosystem. These contributions were instrumental in shaping the MetaSSR framework, enhancing its functionality, and ensuring it meets the needs of developers while demonstrating the power of Metacall and polyglot programming.

### Contributions Before GSoC

- **Adding Rustup and GnuCOBOL as Optional Dependencies in AUR:**
  - Enhanced the MetaCall AUR package by adding `rustup` and `gnucobol` as optional dependencies. This was in response to MetaCall's support for Rust as a loader, ensuring that these dependencies are easily accessible for users.
  - Pull Request: [Add Rustup and GnuCOBOL as Optional Dependencies](https://github.com/metacall/aur/pull/1)


- **Build Fix for ICU4C Version Requirement:**
  - Resolved a critical build issue in the MetaCall core, where the node loader required ICU4C version 73.x or later, fixing the build failure caused by the outdated version 72.x.
  - Pull Request: [Fix Build Issue with ICU4C Version](https://github.com/metacall/core/pull/487)
  - Related Issue: [Build Failure with Node Loader](https://github.com/metacall/core/issues/486)

- **Identifying and Reporting a Segmentation Fault Bug:**
  - Discovered and reported a segmentation fault issue related to a potential deadlock in `function_node_interface_invoke` while conducting benchmarks for the SSR framework project. This bug was critical and needed attention to ensure the stability of the MetaCall integration.
  - Issue Report: [Segmentation Fault (Core Dumped): Potential Deadlock Detected](https://github.com/metacall/core/issues/496)
  - [Source Code](https://github.com/Hulxv/experiments/tree/master/benchmarks) of the experiment that led to this discovery.

- **Benchmarking Metacall with Rust Web Frameworks:** 
  - Conducted performance benchmarks to evaluate the integration of Metacall with various Rust web frameworks, which provided valuable insights for building MetaSSR.
  - Repository: [Metacall Rust HTTP Benchmarks](https://github.com/metacall/rust-http-benchmarks)
  
- **Initializing MetaSSR:**
  - Laid the foundation for the MetaSSR framework by setting up the initial project structure, establishing core concepts, and integrating essential libraries and tools.

- **Tracer and Logger for CLI:**
  - Implemented a robust tracer and logger system for the MetaSSR CLI, improving debugging and providing developers with clear, actionable logs.
  - Pull Request: [CLI Tracer and Logger](https://github.com/hulxv/metassr/pull/2)



### Contributions During GSoC

- **Fixing Script Size Calculation Bug:**
  - Identified and fixed a bug in the MetaCall core that caused scripts loaded from memory to lose their last character due to incorrect size calculation. This issue was critical for ensuring the accurate execution of scripts in memory.
  - Pull Request: [Fix: Incorrectly Calculating the Size of Script Loaded from Memory](https://github.com/metacall/core/pull/514)
  - Related Issue: [Bug: Incorrectly Calculating the Size of Script Loaded from Memory](https://github.com/metacall/core/issues/513)

- **Client Builder Implementation:**
  - Developed the client-side builder, laying the foundation for the SSR and static generation processes within MetaSSR.
  - Pull Request: [Client Builder](https://github.com/metacall/metassr/pull/1)

- **Server-Side Rendering Features:**
  - Implemented core server-side rendering (SSR) features, enabling dynamic content generation on the server for MetaSSR applications.
  - Pull Requests: 
    - [SSR Implementation Part 1](https://github.com/metacall/metassr/pull/2)
    - [SSR Implementation Part 2](https://github.com/metacall/metassr/pull/3)

- **Options for SSR and Static Site Generation:**
  - Added options for both server-side rendering and static-site generation (SSG), allowing developers to choose the rendering strategy that best suits their project.
  - Pull Request: [SSR and SSG Options](https://github.com/metacall/metassr/pull/4)

- **`create` Subcommand for CLI Tool:**
  - Introduced a `create` subcommand in the CLI tool to streamline the process of setting up new MetaSSR projects, making it more accessible to developers.
  - Pull Requests:
    - [Create Subcommand Part 1](https://github.com/metacall/metassr/pull/5)
    - [Create Subcommand Part 2](https://github.com/metacall/metassr/pull/6)

- **Framework Documentation:**
  - Authored comprehensive documentation covering installation, usage, and contribution guidelines, ensuring that developers have the resources they need to effectively use and contribute to MetaSSR.
  - Pull Request: [Framework Documentation](https://github.com/metacall/metassr/pull/7)



## Future Work

Although the GSoC period has ended, there are several areas for further development:

- **Feature Expansion:** Adding support for more languages and frameworks to increase MetaSSR's versatility and appeal.
  
- **Enhanced Tooling:** Continuing to improve the CLI with additional features such as automated deployment options and CI/CD integration.

- **Ongoing Community Support:** Staying engaged with the Metacall community to provide updates, address issues, and implement new features based on user feedback.

## Conclusion

Participating in Google Summer of Code with Metacall has been an incredibly rewarding experience. Building MetaSSR from scratch allowed me to dive deep into SSR frameworks, web development, Rust, and the Metacall ecosystem. I am proud of the progress made and excited to see how MetaSSR will be adopted and extended by the community.

I would like to extend my gratitude to my mentors and the Metacall community for their support and guidance throughout this project. I look forward to continuing my contributions to MetaSSR and other open-source projects in the future.
