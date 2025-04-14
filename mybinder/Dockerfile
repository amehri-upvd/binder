FROM jupyter/base-notebook:python-3.10

USER root

# Copie apt.txt et met à jour les paquets
COPY apt.txt /tmp/
RUN apt-get update && \
    xargs -a /tmp/apt.txt apt-get install -y && \
    apt-get clean

# Copie requirements.yml et configure l'environnement Conda
COPY requirements.yml /tmp/
RUN mamba env update -n base -f /tmp/requirements.yml

# Copie et exécute postBuild
COPY postBuild /tmp/
RUN chmod +x /tmp/postBuild && \
    /tmp/postBuild

USER ${NB_UID}

