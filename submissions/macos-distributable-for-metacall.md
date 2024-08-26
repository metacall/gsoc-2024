**Title:** MacOS Distributable For MetaCall<br>
**Contributor:** [Prakhar Gurunani](https://prakhargurunani.com)<br>
**Mentor:** Vicente Eduardo Ferrer Garcia ([@viferga](https://github.com/viferga))<br>

As a pre-final year undergraduate student at BITS Pilani, I had the incredible opportunity to participate in Google Summer of Code 2024, working on building a MacOS Distributable for MetaCall. Over the course of 18 weeks, I dove deep into the world of cross-platform compatibility, CI/CD pipelines, and open-source development. Today, I'm excited to share my journey and the impact of this project on MetaCall's ecosystem.

## Project Overview

[MetaCall](https://metacall.io), an innovative polyglot runtime, allows developers to write code in multiple programming languages within the same project. My GSoC project aimed to extend MetaCall's cross-platform compatibility by creating a robust MacOS distributable. This involved developing a comprehensive build script, integrating portable dependencies into the CI pipeline, and ensuring seamless functionality across major MacOS versions.

## Key Achievements

### 1. CI Pipeline for MacOS Distributable

One of the primary goals was to create a CI pipeline for compiling and building the distributable binary. We successfully implemented a pipeline that:

- Builds separate binaries for AMD and ARM-based devices using `brew pkg`
- Generates portable distributable that does not require any external dependencies
- Fixed Python dependency issues by using dynamic paths at runtime

The pipeline generates a installable `.pkg` and a portable `.tgz` file, so users can install MetaCall either way.

### 2. Comprehensive Testing Suite

To ensure the reliability of the MacOS distributable, we developed a robust testing pipeline that:

- Verifies the integrity of the distributable using tools like `otool`
- Tests the binary against various MetaCall CLI sub-commands

### 3. Loader Support

During my project, I successfully implemented Python and NodeJS loaders for MetaCall Homebrew formulae along with the support of my mentor. These loaders use their respective runtime as a shared library, which is linked to the object files via `@rpath` declarations, making them portable.

```python
# Change path of shared libraries
change_library_path() {
  loader=$1
  lib_regex=$INSTALL_DIR
  metacall_lib=distributable/metacall-core/lib/lib${loader}_loader.so

  old_lib=$(otool -L "$metacall_lib" | grep -E "$lib_regex" | awk '{print $1}')
  old_lib_regex=$(echo $old_lib | awk -F'/' '{print $(NF-2)"/"$(NF-1)"/"$NF}') # Get the path suffix
  new_lib=$(cd distributable && find . -type f -regex ".*/$old_lib_regex")

  if [ -n "$old_lib" ] && [ -n "$new_lib" ]; then
    install_name_tool -change "$old_lib" "@loader_path/../.$new_lib" "$metacall_lib"
    echo "Updated $loader loader: $old_lib -> $new_lib"
  else
    echo "Failed to update $loader loader: Could not find the old or new library path."
  fi
# }
```

## Challenges and Learnings

Throughout the project, I encountered several challenges that helped me grow as a developer:

1. **Cross-platform Compatibility**: Ensuring that MetaCall worked seamlessly across different MacOS versions and architectures (AMD64 and ARM64) was a complex task. It required a deep understanding of MacOS internals and careful testing.

2. **CI/CD Optimization**: Balancing build times with comprehensive testing was crucial. I learned to optimize the CI pipelines for efficiency without compromising on quality.

3. **Loader Integration**: Each language loader came with its unique set of challenges. Integrating them while maintaining stability was a rewarding experience that enhanced my problem-solving skills.

## Impact and Future Work

This project significantly expands MetaCall's reach by providing native support for MacOS users. Developers can now easily install and use MetaCall on their Mac systems, opening up new possibilities for polyglot development.

Looking ahead, there's potential for further optimization of the build process and expanding support for additional language loaders. The groundwork laid during this project will facilitate easier maintenance and future enhancements of the MacOS distributable.

## Conclusion

Participating in GSoC 2024 with MetaCall has been an incredible learning experience. I've gained invaluable insights into open-source development, cross-platform compatibility, and the intricacies of build systems. I'm grateful to my mentors and the MetaCall community for their guidance and support throughout this journey.

For those interested in exploring the technical details of this project, you can find the main repository [here](https://github.com/metacall/distributable-macos). Contributions to other repositories of MetaCall can be found [here](https://github.com/FirePing32?org=metacall).
