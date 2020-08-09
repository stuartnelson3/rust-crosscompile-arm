# rust cross compiler

taken from https://gitlab.com/Spindel/rust-cross-example

## build

```
docker build -t rust-cross-compiler-arm .
```

## example usage

example usage in a makefile, where current working directory contains your rust code.

note that this caches crates on the local machine for faster builds.

```makefile
CARGO ?= docker run -it --rm \
	-v $(CURDIR):$(CURDIR) \
	-v ~/.cargo/git:/cargo/git \
	-v ~/.cargo/registry:/cargo/registry \
	-w $(CURDIR) stuartnelson3/rust-crosscompiler-arm cargo

build:
  $(CARGO) build --release
```
