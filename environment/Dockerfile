# hash:sha256:f246c23df031619bf610d1a6d8d438d80223cac205c3673b579f431cd1092e22
FROM registry.codeocean.allenneuraldynamics.org/codeocean/jupyterlab:3.6.1-miniconda4.12.0-python3.9-ubuntu20.04

ARG DEBIAN_FRONTEND=noninteractive

ARG GIT_ASKPASS
ARG GIT_ACCESS_TOKEN
COPY git-askpass /

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential=12.8ubuntu1.1 \
    && rm -rf /var/lib/apt/lists/*

RUN conda install -y --channel=conda-forge \
        bottleneck==1.3.5 \
        dask==2023.8.1 \
        matplotlib==3.7.1 \
        netcdf4==1.6.2 \
        networkx==2.8.8 \
        numpy==1.24.4 \
        pip==23.2.1 \
        scikit-learn==1.3.0 \
        seaborn==0.12.2 \
        setuptools==65.6.3 \
        xarray==2023.8.0 \
    && conda clean -ya

RUN pip install -U --no-cache-dir \
    caveclient==5.10.1 \
    dotmotif==0.13.0 \
    meshparty==1.16.14 \
    nglui==2.14.3 \
    standard-transform==1.4.0

COPY postInstall /
RUN /postInstall
