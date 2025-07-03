# Base Python image
FROM python:3.12-alpine
# Install requirements for non-root user sudo privileges
ARG USERNAME=mkdocs
RUN apk update \
    && apk add --no-cache \
    sudo \
    git \
    curl \
    bash \
    && rm -rf /var/cache/apk/*
# Create a non-root user with sudo privileges
RUN adduser -D -s /bin/bash ${USERNAME} \
    && echo "${USERNAME} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers \
    && mkdir -p /home/${USERNAME}/.local/bin \
    && chown -R ${USERNAME}:${USERNAME} /home/${USERNAME} \
    && echo "export PATH=/home/${USERNAME}/.local/bin:\$PATH" >> /home/${USERNAME}/.bashrc
# Switch to the non-root user
USER ${USERNAME}

# Install mkdocs and material theme plus common extensions
RUN pip install --upgrade pip \
    && pip install mkdocs mkdocs-material pymdown-extensions

# Set working directory for the workspace
WORKDIR /app

# Expose MkDocs dev server port
EXPOSE 8000

# Default command: serve the documentation on all interfaces
CMD ["sh", "-c", "pip install -r requirements.txt && python -m mkdocs serve --dev-addr=0.0.0.0:8000"]