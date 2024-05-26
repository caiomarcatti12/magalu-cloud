FROM alpine:3.20.0

# Atualiza os índices de pacote do Alpine e instala as versões específicas
# dos pacotes curl, wget e tar, sem guardar o cache dos pacotes para reduzir o tamanho.
RUN apk update && \
    apk add --no-cache \
    curl=8.7.1-r0 \
    wget=1.24.5-r0 \
    tar=1.35-r2

# Baixa o arquivo tar.gz do mgccli do GitHub de forma silenciosa, extrai o conteúdo,
# move o executável para /usr/local/bin, dá permissão de execução e remove os arquivos temporários.
RUN wget https://github.com/MagaluCloud/mgccli/releases/download/v0.18.10/mgccli_0.18.10_linux_amd64.tar.gz --quiet && \
    tar -xzf mgccli_0.18.10_linux_amd64.tar.gz -C /tmp && \
    mv /tmp/mgc /usr/local/bin/mgc && \
    chmod +x /usr/local/bin/mgc && \
    rm -rf /tmp/*

# Cria um usuário chamado 'non-root-user' com UID 1001 sem criar um diretório home padrão.
RUN adduser -D -u 1001 non-root-user

# O container escutará na porta 8095.
EXPOSE 8095

# O container será executado como o usuário 'non-root-user'.
USER non-root-user

# Define o diretório de trabalho para /home/non-root-user.
WORKDIR /home/non-root-user

# Define o comando padrão e o shell para execução.
CMD ["/bin/sh"]
