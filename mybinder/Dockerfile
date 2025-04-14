FROM jupyter/base-notebook:python-3.10

# Installer les dépendances système
USER root
COPY apt.txt /tmp/
RUN apt-get update && \
    xargs -a /tmp/apt.txt apt-get install -y --no-install-recommends && \
    apt-get clean

# Configurer l'environnement Conda
COPY requirements.yml /tmp/
RUN mamba env update -n base -f /tmp/requirements.yml

# Copier et exécuter postBuild
COPY postBuild /tmp/
RUN chmod +x /tmp/postBuild && \
    /tmp/postBuild

USER ${NB_UID}

