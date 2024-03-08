# You can pick any Debian/Ubuntu-based image. 😊
FROM mcr.microsoft.com/devcontainers/python:3

# Upgrade and install additional packages
RUN apt-get update && apt-get install -y \
    git \
    wget \
    direnv \
    yq \
    && rm -rf /var/lib/apt/lists/*

# Set up direnv hook
RUN echo 'eval "$(direnv hook bash)"' >> ~/.bashrc
RUN echo 'eval "$(direnv hook bash)"' >> ~/.bash_profile

# Add tfenv to manage terraform environment
RUN git clone --depth=1 https://github.com/tfutils/tfenv.git ~/.tfenv \
    && echo 'export PATH="$HOME/.tfenv/bin:$PATH"' >> ~/.bash_profile \
    && echo 'export PATH="$HOME/.tfenv/bin:$PATH"' >> ~/.zprofile

# Install GitLab runner
RUN curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh" | sudo bash \
    && sudo apt-get install gitlab-runner

# Install Taskfile
RUN sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b ~/.local/bin

# Install checkov
RUN pip install checkov