# Installation

```{note}
Support for building from source on Windows is currently work in progress. 
```

## Prerequisites

Install the latest stable [Rust](https://www.rust-lang.org/tools/install). If Rust is already installed, please ensure you are using the latest stable version via:
```bash
rustup update stable
```

Install [CMake](https://cmake.org/install/).


## Build Hyperon library from source

Clone the [OpenCog Hyperon repository](https://github.com/trueagi-io/hyperon-experimental):

```bash
git clone https://github.com/trueagi-io/hyperon-experimental.git
```

Build and test the library:

```bash
cd ./lib
cargo build 
cargo test
```

To enable logging during tests, execute this instead:

```bash
RUST_LOG=hyperon=debug cargo test
```

To generate the API docs, execute (under the `lib` directory):

```bash
cargo doc
```

Docs can then be found at `./lib/target/doc/hyperon/index.html`.


## Build C and Python API

Next, install the following Rust and Python libraries (must be executed in the root directory of the repository):

```bash
cargo install --force cbindgen
python -m pip install conan==1.47
python -m pip install -e ./python[dev]
```

Configure Conan for CMake:

`````{tabs}
````{tab} Linux

On Linux, first find out your `gcc` version via:

```bash
gcc --version
```

Then, run the following command to configure Conan:

```bash
conan profile update settings.compiler=gcc default
conan profile update settings.compiler.version=<your gcc version> default
conan profile update settings.compiler.libcxx=libstdc++ default
```

````

````{tab} Mac OS

On Mac OS, find out your `clang` version via:

```bash
clang --version
```

Then, run the following command to configure Conan:
```bash
conan profile update settings.compiler=clang default
conan profile update settings.compiler.version=<your clang version> default  
conan profile update settings.compiler.libcxx=libc++ default 
```

````
`````

Then, setup the build via CMake:

```bash
mkdir -p build
cd build
cmake ..
```

````{note}
To run release build, use the following instead of `cmake ..`:

```bash
cmake -DCMAKE_BUILD_TYPE=Release ..
```

````

Build the API and run tests:
```bash
make
make check
```

## Running Python examples from command line

In order to run Python examples, you need to add Python libraries into the `PYTHONPATH` environment variable after compilation:

```bash
cd build
export PYTHONPATH=$PYTHONPATH:`pwd`/python:`pwd`/../python
```

## Language support for IDEs [Optional]

Different IDEs may require different tweaks to support the languages
used in the codebase. The language servers which we use
for development are:
- [Rust Language Server](https://github.com/rust-lang/rls#setup);
- [clangd](https://clangd.llvm.org/installation), generate compile
  commands for the `clangd` using `cmake` variable:
  ```
  cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=Y ..
  ```
- [Python LSP server](https://github.com/python-lsp/python-lsp-server#installation).


# Docker Image

Alternatively, instead of building from source, a docker image can be used to run a reproducible environment. See instructions inside the [Dockerfile](https://github.com/trueagi-io/hyperon-experimental/blob/main/.github/Dockerfile).
If the docker image doesn't work, please
raise an
[issue](https://github.com/trueagi-io/hyperon-experimental/issues).

