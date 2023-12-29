FROM archlinux:base-devel

ARG USERNAME=ggm
ARG USER_HOME=/home/${USERNAME}

RUN /usr/sbin/bash -c "pacman -Syu --noconfirm" && \
    pacman -S git --noconfirm && \
    pacman -S wget --noconfirm && \
    pacman -S zsh --noconfirm && \
    pacman -S vim --noconfirm && \
    pacman -S hugo --noconfirm && \
    useradd -m -s /usr/sbin/zsh ${USERNAME} && \
    pacman -Sc

USER $USERNAME
WORKDIR $USER_HOME

RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
RUN git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
RUN git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
RUN git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf

COPY --chown=${USERNAME}:${USERNAME} .devcontainer/resources/sample-zshrc $USER_HOME/.zshrc
COPY --chown=${USERNAME}:${USERNAME} .devcontainer/resources/sample-zshenv $USER_HOME/.zshenv
COPY --chown=${USERNAME}:${USERNAME} .devcontainer/resources/sample-p10k-zsh $USER_HOME/.p10k.zsh