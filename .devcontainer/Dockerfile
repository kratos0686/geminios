# Use Ubuntu 22.04 LTS as base for OS development
FROM ubuntu:22.04

# Avoid prompts from apt
ENV DEBIAN_FRONTEND=noninteractive

# Install essential OS development tools
RUN apt-get update && apt-get install -y \
    # Build essentials
    build-essential \
    gcc \
    g++ \
    clang \
    llvm \
    make \
    cmake \
    ninja-build \
    autoconf \
    automake \
    libtool \
    pkg-config \
    # Kernel development tools
    linux-headers-generic \
    libelf-dev \
    libssl-dev \
    bc \
    flex \
    bison \
    # Version control
    git \
    git-lfs \
    # Debugging tools
    gdb \
    lldb \
    valgrind \
    strace \
    # System utilities
    vim \
    nano \
    curl \
    wget \
    zip \
    unzip \
    tar \
    # Python for build scripts
    python3 \
    python3-pip \
    python3-dev \
    # Cross-compilation tools (for ARM Chromebooks)
    gcc-arm-linux-gnueabihf \
    g++-arm-linux-gnueabihf \
    gcc-aarch64-linux-gnu \
    g++-aarch64-linux-gnu \
    # Additional utilities
    tree \
    htop \
    man-db \
    manpages-dev \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Set up working directory
WORKDIR /workspace

# Switch to non-root user
USER $USERNAME

# Set environment variables
ENV PATH="/home/$USERNAME/.local/bin:${PATH}"

# Install Python packages that might be useful for OS development
RUN pip3 install --user \
    meson \
    && echo 'alias ll="ls -alF"' >> ~/.bashrc \
    && echo 'alias la="ls -A"' >> ~/.bashrc \
    && echo 'export PS1="\[\e[32m\][Geminios]\[\e[m\] \[\e[34m\]\w\[\e[m\] \$ "' >> ~/.bashrc

CMD ["/bin/bash"]