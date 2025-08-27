# Start from miniconda base image
FROM continuumio/miniconda3:latest

# Install build tools (needed for JIT compilation in FEniCSx)
RUN apt-get update && apt-get install -y --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /pv-pvlib

# Install packages from conda-forge
RUN pip install pvlib[optional] \
    && conda clean -afy


