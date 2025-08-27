FROM opencfd/openfoam-default:2412 AS build

# Set environment variables for cfMesh location
ENV CFMESH_DIR=/opt/cfmesh

# Install build dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    git cmake build-essential flex bison zlib1g-dev \
  && rm -rf /var/lib/apt/lists/*

# Clone cfMesh source into designated directory
RUN mkdir -p /opt/cfmesh
RUN git clone --branch development --single-branch https://github.com/pawansnegi/cfMesh.git /opt/cfmesh

# Build cfMesh
WORKDIR /opt/cfmesh
RUN ls -la > /opt/cfmesh/files.txt
RUN  bash -lc "source /usr/lib/openfoam/openfoam2412/etc/bashrc && ./Allwmake"


ENV CFMESH_DIR=/root/OpenFOAM/user-v2412/platforms/linux64GccDPInt32Opt
ENV PATH="${PATH}:${CFMESH_DIR}/bin"
ENV LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:${CFMESH_DIR}/lib"

# Always source OpenFOAM when opening bash
# RUN echo "source /usr/lib/openfoam/openfoam2412/etc/bashrc" >> /etc/bash.bashrc

WORKDIR /home
ENV HOME=/home
# Default working directory (for volume mounting cases)