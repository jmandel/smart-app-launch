ARG VARIANT=11-jdk-buster
ARG NODE_VERSION=16

FROM mcr.microsoft.com/vscode/devcontainers/java:0-${VARIANT}

RUN apt-get update && apt-get -y install python3 python3-pip gosu openssl wget graphviz

ENV PATH="/usr/local/rvm/bin:/usr/local/rvm/rubies/ruby-2.5.1/bin:${PATH}"
RUN gpg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB && \
    curl -L get.rvm.io | bash -s stable  && \
    rvm install 2.5.1 && \
    gem install jekyll jekyll-asciidoc

RUN mkdir /home/vscode/ && chown vscode.vscode -R /home/vscode && npm install -g fsh-sushi

USER vscode

# Latest fsh and ig-publisher-scripts each time we start
RUN mkdir -p /home/vscode/bin && \
    cd /home/vscod/bin && \
    git clone https://github.com/HL7/ig-publisher-scripts
