# Base Python image
FROM squidfunk/mkdocs-material
# Install requirements for non-root user sudo privileges
RUN apk update \
    && apk add --no-cache \
    sudo \
    git \
    curl \
    bash \
    && rm -rf /var/cache/apk/*
# Install Python 3 and pip
RUN apk add --no-cache python3 py3-pip \
    && ln -sf python3 /usr/bin/python \
    && pip install --upgrade pip
# Create a non-root user with sudo privileges
RUN adduser -D -s /bin/bash vscode \
    && echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers \
    && mkdir -p /home/vscode/.local/bin \
    && chown -R vscode:vscode /home/vscode
# Switch to the non-root user
USER vscode

# Install mkdocs and material theme plus common extensions
RUN pip install --upgrade pip \
    && pip install mkdocs mkdocs-material pymdown-extensions

# Set working directory for the workspace
WORKDIR /workspace

# Expose MkDocs dev server port
EXPOSE 8000

# Default command: serve the documentation on all interfaces
CMD ["serve", "--dev-addr=0.0.0.0:8000"]