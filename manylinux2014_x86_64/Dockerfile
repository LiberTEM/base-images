FROM quay.io/pypa/manylinux2014_x86_64

ENV LIBCLANG_PATH=/opt/rh/llvm-toolset-7/root/usr/lib64
ENV BINDGEN_C_INCLUDE_PATH=/opt/rh/llvm-toolset-7/root/usr/lib64/clang/5.0.1/include

RUN yum install -y llvm-toolset-7-clang-devel && yum clean all

# install rust into the image.
# adapted from https://github.com/rust-lang/docker-rust/blob/master/1.65.0/bullseye/slim/Dockerfile
ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    PATH=/usr/local/cargo/bin:$PATH \
    RUST_VERSION=1.65.0

RUN set -eux; \
    arch="$(uname -m)"; \
    case "${arch}" in \
        x86_64) rustArch='x86_64-unknown-linux-gnu'; rustupSha256='5cc9ffd1026e82e7fb2eec2121ad71f4b0f044e88bca39207b3f6b769aaa799c' ;; \
        *) echo >&2 "unsupported architecture: ${dpkgArch}"; exit 1 ;; \
    esac; \
    url="https://static.rust-lang.org/rustup/archive/1.25.1/${rustArch}/rustup-init"; \
	curl -o  rustup-init "$url"; \
    echo "${rustupSha256} *rustup-init" | sha256sum -c -; \
    chmod +x rustup-init; \
        ./rustup-init -y --no-modify-path --profile minimal --default-toolchain $RUST_VERSION --default-host ${rustArch}; \
    rm rustup-init; \
    chmod -R a+w $RUSTUP_HOME $CARGO_HOME; \
    rustup --version; \
    cargo --version; \
    rustc --version;
