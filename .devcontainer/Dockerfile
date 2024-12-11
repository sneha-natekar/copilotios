# Use the official Swift image as a base image
FROM swift:latest

# Install dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    unzip \
    libssl-dev \
    libcurl4-openssl-dev \
    zlib1g-dev \
    libsqlite3-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Xcode command line tools
RUN xcode-select --install

# Set up environment variables
ENV SWIFT_VERSION=latest
ENV XCODE_VERSION=latest

# Install Swift
RUN curl -s https://swift.org/builds/swift-$SWIFT_VERSION-release/ubuntu1804/swift-$SWIFT_VERSION-RELEASE/swift-$SWIFT_VERSION-RELEASE-ubuntu18.04.tar.gz | tar xz -C /usr/local --strip-components=1

# Install other relevant tools for iOS development
RUN apt-get update && apt-get install -y \
    vim \
    nano \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /workspace

# Copy the current directory contents into the container at /workspace
COPY . /workspace

# Run the Swift REPL by default
CMD ["swift"]
