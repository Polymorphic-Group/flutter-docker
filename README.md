# Flutter Docker Image

This repository contains a GitHub Actions workflow to build and push a Docker image for a Flutter application to GitHub Container Registry.

## Usage

To use this Docker image in your own Dockerfile, follow the steps below:

1. **Pull the Docker image from GitHub Container Registry:**

   You can pull the Docker image using the following command:

   ```sh
   docker pull ghcr.io/Polymorphic-Group/flutter:latest
   ```

2. **Use the Docker image as a base image in your Dockerfile:**

Create a Dockerfile in your project and use the pulled image as the base image:
```dockerfile
# Use the Flutter Docker image from GitHub Container Registry
FROM ghcr.io/Polymorphic-Group/flutter:latest

# Set the working directory
WORKDIR /app

# Copy your Flutter project files to the container
COPY . .

# Install dependencies
RUN flutter pub get

# Build the Flutter project
RUN flutter build apk --release

# Specify the command to run your application
CMD ["flutter", "run"]
```

3. **Build your Docker image:**

Run the following command to build your Docker image:
```sh
docker build -t my-flutter-app .
```

4. Run your Docker container:

Run the following command to start a container from your Docker image:
```sh
docker run -p 8080:8080 my-flutter-app
```

## License

This project is licensed under a proprietary license. All rights are reserved. You may not copy, modify, or distribute this code without permission from the author.