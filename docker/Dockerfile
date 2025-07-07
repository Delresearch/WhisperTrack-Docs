# Base Python image
FROM python:3.12-slim
# Install requirements for non-root user sudo privileges
ARG USERNAME=mkdocs
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    sudo \
    git \
    curl \
    bash \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
# Create a non-root user with sudo privileges
RUN useradd -ms /bin/bash ${USERNAME} \
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
COPY --chown=${USERNAME}:${USERNAME} . /app
# Expose MkDocs dev server port
EXPOSE 8000

# Default command: serve the documentation on all interfaces
CMD ["sh", "-c", "pip install -r requirements.txt && python -m mkdocs serve --dev-addr=0.0.0.0:8000"]