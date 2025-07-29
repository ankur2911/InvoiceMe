FROM ubuntu:22.04

# Install dependencies for Flutter
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    xz-utils \
    zip \
    libglu1-mesa \
    openjdk-11-jdk \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Install Flutter SDK
RUN git clone https://github.com/flutter/flutter.git /usr/local/flutter -b stable
ENV PATH="/usr/local/flutter/bin:/usr/local/flutter/bin/cache/dart-sdk/bin:${PATH}"

# Accept Android licenses (optional, if you want Android builds)
RUN yes | /usr/local/flutter/bin/flutter doctor --android-licenses

# Pre-cache Flutter artifacts (optional but speeds up first run)
RUN flutter precache

# Run flutter doctor to validate
RUN flutter doctor

# Set working directory
WORKDIR /workspace

# Expose port for Flutter web
EXPOSE 8080
