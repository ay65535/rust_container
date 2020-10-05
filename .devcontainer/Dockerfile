# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.145.0/containers/rust/.devcontainer/base.Dockerfile

FROM mcr.microsoft.com/vscode/devcontainers/rust:0-1

ENV https_proxy=$https_proxy
ENV http_proxy=$http_proxy

# [Optional] Uncomment this section to install additional packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# https://code.visualstudio.com/docs/remote/containers-advanced#_avoiding-extension-reinstalls-on-container-rebuild
# RUN mkdir -p /home/$USERNAME/.vscode-server/extensions /home/$USERNAME/.vscode-server-insiders/extensions \
#     && chown -R $USERNAME /home/$USERNAME/.vscode-server /home/$USERNAME/.vscode-server-insiders

# preserve .bash_history
RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
    && echo $SNIPPET >> "/root/.bashrc"
    #  \
    # [Optional] If you have a non-root user
    # && mkdir /commandhistory \
    # && touch /commandhistory/.bash_history \
    # && chown -R $USERNAME /commandhistory \
    # && echo $SNIPPET >> "/home/$USERNAME/.bashrc"
