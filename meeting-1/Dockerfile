# Use the latest Ubuntu as base
FROM ubuntu:latest

# Avoid interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies, add Helix PPA, and install our tools
RUN apt-get update && apt-get install -y software-properties-common \
    && add-apt-repository ppa:maveonair/helix-editor -y \
    && apt-get update && apt-get install -y \
    zsh \
    git \
    curl \
    helix \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Create a standard user (dev)
RUN useradd -m -s /bin/zsh dev && \
    echo "dev ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Log in as the new user
USER dev
WORKDIR /home/dev

RUN cat <<EOF > ~/.zshrc
# Init Zsh
PROMPT='%n@macbook %~ %# '
alias reload="source ~/.zshrc"
EOF

# Start directly in a bare Zsh shell
CMD ["zsh"]
