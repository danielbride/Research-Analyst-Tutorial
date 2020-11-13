FROM rocker/binder:3.6.3

## Declares build arguments
ARG NB_USER
ARG NB_UID

USER root
COPY . ${HOME}
RUN chown -R ${NB_USER} ${HOME}

CMD jupyter notebook --ip 0.0.0.0

## Become normal user again
USER ${NB_USER}

## Run an install.R script, if it exists.
RUN if [ -f install.R ]; then R --quiet -f install.R; fi

WORKDIR /home/${NB_USER}