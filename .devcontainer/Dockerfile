ARG VARIANT=11-jdk-buster

FROM mcr.microsoft.com/vscode/devcontainers/java:0-${VARIANT}
RUN apt-get update && apt-get -y install python3 python3-pip gosu openssl wget graphviz ruby jekyll
ENV PATH="/usr/local/rvm/bin:/usr/local/rvm/rubies/ruby-2.5.1/bin:${PATH}"

USER vscode

# Latest fsh and ig-publisher-scripts each time we start
RUN cd /tmp && \
    git clone https://github.com/HL7/ig-publisher-scripts && \
    cd ig-publisher-scripts && \
    mkdir -p ~/.local/bin && \
    cp *.sh ~/.local/bin && \
    cd /tmp && \
    rm -rf ig-publisher-scripts && \
    . /usr/local/share/nvm/nvm.sh && \
    nvm install 16 && \
    npm install -g fsh-sushi && \
    npm install -g http-server

