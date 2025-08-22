ARG VARIANT="bookworm"
FROM mcr.microsoft.com/devcontainers/base:bookworm

ENV DEBIAN_FRONTEND=noninteractive
ENV USERNAME=vscode

SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN \
    # Set password for user to be the same as the username
    echo "${USERNAME}:${USERNAME}" | chpasswd && \
    # Add user to sudoers
    echo "${USERNAME} ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/${USERNAME} && \
    # Set user's default shell to zsh
    chsh -s /usr/bin/zsh ${USERNAME}

# Recursive copy with merge existing files
COPY --chown=${USERNAME}:${USERNAME} ./dotfiles/. /home/${USERNAME}/
