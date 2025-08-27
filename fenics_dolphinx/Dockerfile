# Start from miniconda base image
FROM continuumio/miniconda3:latest

# Install build tools (needed for JIT compilation in FEniCSx)
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        gcc \
        g++ \
        cmake \
        pkg-config \
    && rm -rf /var/lib/apt/lists/*
# Set working directory
WORKDIR /app

# Install packages from conda-forge
RUN conda install -y -c conda-forge fenics-dolfinx mpich pyvista \
    && conda clean -afy

# Set workdir inside container
WORKDIR /pv-fenics

# # Set default command
# CMD ["python", "main.py"]

