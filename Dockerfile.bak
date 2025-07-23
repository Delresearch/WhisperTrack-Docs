FROM squidfunk/mkdocs-material:latest
# Install dependencies
RUN apk update && \
    apk add --no-cache bash
COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt
