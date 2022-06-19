# move to guide base dir
mkdir Step{$Number}_build
cd Step{$Number}_build

# 初始化构建系统
样例：cmake ../Step{$Number}_build

```shell

Usage

cmake [options] <path-to-source>
cmake [options] <path-to-existing-build>
cmake [options] -S <path-to-source> -B <path-to-build>

Specify a source directory to (re-)generate a build system for it in the
current working directory.  Specify an existing build directory to
re-generate its build system.

Run 'cmake --help' for more information.
```


# 构建当前项目
样例：cmake --build <dir> [options]

```shell
Usage: cmake --build <dir>             [options] [-- [native-options]]
cmake --build --preset <preset> [options] [-- [native-options]]
Options:
  <dir>          = Project binary directory to be built.
  --preset <preset>, --preset=<preset>
                 = Specify a build preset.
  --list-presets
                 = List available build presets.
  --parallel [<jobs>], -j [<jobs>]
                 = Build in parallel using the given number of jobs. 
                   If <jobs> is omitted the native build tool's 
                   default number is used.
                   The CMAKE_BUILD_PARALLEL_LEVEL environment variable
                   specifies a default parallel level when this option
                   is not given.
  --target <tgt>..., -t <tgt>... 
                 = Build <tgt> instead of default targets.
  --config <cfg> = For multi-configuration tools, choose <cfg>.
  --clean-first  = Build target 'clean' first, then build.
                   (To clean only, use --target 'clean'.)
  --verbose, -v  = Enable verbose output - if supported - including
                   the build commands to be executed. 
  --             = Pass remaining options to the native tool.
```



# 安装当前项目
样例：cmake --install . --prefix "../Step5_install"

```shell
Usage: cmake --install <dir> [options]
Options:
  <dir>              = Project binary directory to install.
  --config <cfg>     = For multi-configuration tools, choose <cfg>.
  --component <comp> = Component-based install. Only install <comp>.
  --default-directory-permissions <permission> 
     Default install permission. Use default permission <permission>.
  --prefix <prefix>  = The installation prefix CMAKE_INSTALL_PREFIX.
  --strip            = Performing install/strip.
  -v --verbose       = Enable verbose output.
```

#
