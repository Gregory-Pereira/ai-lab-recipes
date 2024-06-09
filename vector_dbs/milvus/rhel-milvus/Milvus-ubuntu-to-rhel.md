Ubuntu deps:
    - g++ gcc gdb gdbserver ninja-build git make ccache libssl-dev zlib1g-dev zip unzip \
    clang-format-10 clang-tidy-10 lcov libtool m4 autoconf automake python3 python3-pip \
    pkg-config uuid-dev libaio-dev libopenblas-dev

in progress deps:
    - ccache \
    clang-format-10 clang-tidy-10 lcov \
    libaio-dev libopenblas-dev

Dont need:
    - python3 python3-pip

Already installed:
    - g++, gcc, gdb, git, make, zip, unzip, m4, autoconf automake

Can be installed regularly:
    - ninja-build, gdb-gdbserver, libtool

RHEL equivalents of Ubuntu packages (Ubuntu --> RHEL):
    - gdbserver --> gdb-gdbserver
    - libssl-dev --> openssl-devel
    - zlib1g-dev --> zlib-devel
    - pkg-config --> pkgconf-pkg-config
    - uuid-dev --> libuuid-devel
    
RHEL equivalents that dont exist:
    - libaio-dev --> libaio (devel option does not exist)
    - libopenblas-dev --> openblas

Needs to be installed manually:
    - ccache

Not sure what this is:
    - lcov

Issues:
    - lcov has a perl dependency and resolving this is difficult
        - 