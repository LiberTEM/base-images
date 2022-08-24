FROM quay.io/pypa/manylinux2014_x86_64

ENV LIBCLANG_PATH=/opt/rh/llvm-toolset-7/root/usr/lib64

RUN yum install -y llvm-toolset-7-clang-devel && yum clean all
