FROM mambaorg/micromamba

ARG QUARTO_VERSION=1.3.450
USER root
RUN apt-get update && apt-get install -y curl && curl -fsSL https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VERSION}/quarto-${QUARTO_VERSION}-linux-amd64.deb -o quarto.deb && \
  dpkg -i quarto.deb
USER mambauser


COPY --chown=$MAMBA_USER:$MAMBA_USER env.yml /tmp/env.yml
RUN micromamba install -y -n base -f /tmp/env.yml && \
    micromamba clean --all --yes


RUN echo "PS1='🐳 \[\033[1;36m\]\h \[\033[1;34m\]\W\[\033[0;35m\] \[\033[1;93m\]# \[\033[0m\]'" >> ~/.bashrc