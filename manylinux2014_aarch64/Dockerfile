FROM quay.io/pypa/manylinux2014_aarch64

ENV LIBCLANG_PATH=/opt/rh/llvm-toolset-7.0/root/usr/lib64
ENV BINDGEN_C_INCLUDE_PATH=/opt/rh/llvm-toolset-7.0/root/usr/lib64/clang/7.0.1/include

RUN yum install -y centos-release-scl && yum install -y llvm-toolset-7.0-clang-devel && yum clean all
