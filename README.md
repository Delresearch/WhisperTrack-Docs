# WhisperTrack-Docs
## Running WhisperTrack Docs
### Requirements
- [Docker](https://docs.docker.com/engine/install/)
#### Clone Repository
```bash
git clone https://github.com/Delresearch/WhisperTrack-Docs
cd WhisperTrack-Docs
```
#### Build the Docker Image
```bash
docker build -t whispertrackdocs -f docker/Dockerfile .
```
#### Run the container
```bash
docker run -it --rm -p 8000:8000 --name=whispertrackdocs whispertrackdocs
```
This will start the documentation server and make it available at `http://localhost:8000`.
## Development
### VSCode dev container
If you are using VSCode, you can use the dev container to run the documentation server. This will automatically install all dependencies and set up the environment for you.
1. Open the repository in VSCode.
2. Install the Remote - Containers extension if you haven't already.
3. Open the Command Palette (Ctrl+Shift+P) and select "Remote-Containers: Reopen in Container".
4. Once the container is built, you can run the documentation server using the terminal inside the container:
```bash
mkdocs serve
```
This will start the documentation server and make it available at `http://localhost:8000`.
### Docker Container Development
If you prefer to run the documentation server locally without using VSCode, you can follow these steps to run the site:
[Running WhisperTrack Docs](#running-whispertrack-docs)
#### Attach to the container
```bash
docker exec -it whispertrackdocs /bin/bash
```
## Contributing
We welcome contributions to the WhisperTrack documentation! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.