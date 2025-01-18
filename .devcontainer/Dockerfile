ARG PYTHON_VERSION=3.12
FROM mcr.microsoft.com/devcontainers/python:1-${PYTHON_VERSION}

# Install pylint
RUN pip install pylint

# Configure apt
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
  && apt-get -y install --no-install-recommends apt-utils 2>&1

# Install git, process tools, lsb-release (common in install instructions for CLIs)
RUN apt-get -y install git procps lsb-release

# Install any missing dependencies for enhanced language service
RUN apt-get install -y libicu[0-9][0-9]

RUN mkdir /workspace
WORKDIR /workspace

# Clean up
RUN apt-get autoremove -y \
  && apt-get clean -y \
  && rm -rf /var/lib/apt/lists/*
ENV DEBIAN_FRONTEND=dialog

# Set the default shell to bash rather than sh
ENV SHELL /bin/bash
