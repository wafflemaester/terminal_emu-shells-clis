# Use Ubuntu as the base image
FROM ubuntu:latest

# Prevent interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# 1. Install prerequisites
RUN apt-get update && apt-get install -y \
    software-properties-common \
    curl \
    git \
    sudo \
    ca-certificates \
    tar \
    && add-apt-repository ppa:maveonair/helix-editor -y \
    && apt-get update && apt-get install -y helix \
    # 2. Automatically detect architecture and download the correct Nushell
    && ARCH=$(uname -m) && \
    if [ "$ARCH" = "x86_64" ]; then \
        URL="https://github.com/nushell/nushell/releases/download/0.91.0/nu-0.91.0-x86_64-unknown-linux-gnu.tar.gz"; \
        DIR="nu-0.91.0-x86_64-unknown-linux-gnu"; \
    else \
        URL="https://github.com/nushell/nushell/releases/download/0.91.0/nu-0.91.0-aarch64-unknown-linux-gnu.tar.gz"; \
        DIR="nu-0.91.0-aarch64-unknown-linux-gnu"; \
    fi && \
    curl -L $URL -o nushell.tar.gz && \
    tar -xzf nushell.tar.gz && \
    mv $DIR/nu /usr/bin/nu && \
    rm -rf nushell.tar.gz $DIR \
    && rm -rf /var/lib/apt/lists/*

# 3. Create a standard dev user
RUN useradd -m -s /usr/bin/nu dev && \
    echo "dev ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER dev
WORKDIR /home/dev

# 4. Configure Nushell (disable banner and add reload alias)
RUN mkdir -p /home/dev/.config/nushell && \
    touch /home/dev/.config/nushell/env.nu && \
    cat <<EOF > /home/dev/.config/nushell/config.nu
\$env.config = {
    show_banner: false,
}

# Your reload shortcut
alias reload = source ~/.config/nushell/config.nu
EOF

# Start directly in Nushell
CMD ["nu"]