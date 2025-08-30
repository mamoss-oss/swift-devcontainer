FROM mcr.microsoft.com/devcontainers/base:ubuntu

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    gpg \
    curl \
    wget \
    git \
    vim-tiny \
    iputils-ping \
    net-tools \
    procps \
    libpython3-dev \
    libxml2-dev \
    libncurses-dev \
    libz3-dev \
    pkg-config && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*


USER vscode
WORKDIR /home/vscode
RUN curl -O https://download.swift.org/swiftly/linux/swiftly-$(uname -m).tar.gz
RUN tar zxf swiftly-$(uname -m).tar.gz  && \
    ./swiftly init --assume-yes  --verbose && \
    rm swiftly-$(uname -m).tar.gz

# Bash completions
RUN mkdir -p $HOME/.local/share/bash-completion/completions && \
    $HOME/.local/share/swiftly/bin/swift package completion-tool generate-bash-script > $HOME/.local/share/bash-completion/completions/swift && \
    $HOME/.local/share/swiftly/bin/swiftly --generate-completion-script bash > $HOME/.local/share/bash-completion/completions/swiftly

# .bashrc additions
RUN cat <<'EOF' >> $HOME/.bashrc
# ---- Custom Section Start ----
export PATH="$PATH:$HOME/.local/share/swiftly/bin"

# Load local bash completions
if [ -d "$HOME/.local/share/bash-completion/completions" ]; then
  for comp in "$HOME/.local/share/bash-completion/completions/"*; do
    [ -f "$comp" ] && . "$comp"
  done
fi
# ---- Custom Section End ----
EOF

# Optional install static linux sdk
# The sdk version needs to match the installed swift version.
# Copy an up to date install command from https://www.swift.org/install/linux/ - Change swift to $HOME/.local/share/swiftly/bin/swift
# swift sdk install https://download.swift.org/swift-6.1.2-release/static-sdk/swift-6.1.2-RELEASE/swift-6.1.2-RELEASE_static-linux-0.0.1.artifactbundle.tar.gz --checksum df0b40b9b582598e7e3d70c82ab503fd6fbfdff71fd17e7f1ab37115a0665b3b
