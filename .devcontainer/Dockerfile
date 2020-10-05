# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.145.0/containers/rust/.devcontainer/base.Dockerfile

FROM mcr.microsoft.com/vscode/devcontainers/rust:0-1

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive \
    https_proxy=${https_proxy} \
    http_proxy=${http_proxy}

# This Dockerfile adds a non-root 'vscode' user with sudo access. However, for Linux,
# this user's GID/UID must match your local user UID/GID to avoid permission issues
# with bind mounts. Update USER_UID / USER_GID if yours is not 1000. See
# https://aka.ms/vscode-remote/containers/non-root-user for details.
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ARG http_proxy
ARG https_proxy

# [Optional] Uncomment this section to install additional packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# https://code.visualstudio.com/docs/remote/containers-advanced#_avoiding-extension-reinstalls-on-container-rebuild
RUN mkdir -p /home/$USERNAME/.vscode-server/extensions /home/$USERNAME/.vscode-server-insiders/extensions \
    && chown -R $USERNAME /home/$USERNAME/.vscode-server /home/$USERNAME/.vscode-server-insiders

# preserve .bash_history
RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
    && echo $SNIPPET >> "/root/.bashrc" \
    # [Optional] If you have a non-root user
    && mkdir /commandhistory \
    && touch /commandhistory/.bash_history \
    && chown -R $USERNAME /commandhistory \
    && echo $SNIPPET >> "/home/$USERNAME/.bashrc"

USER vscode
ENV HOME /home/$USERNAME

# Switch back to dialog for any ad-hoc use of apt-get
ENV DEBIAN_FRONTEND=
