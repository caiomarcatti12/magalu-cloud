# Docker Container para MGC CLI da Magalu Cloud

Este container Docker encapsula o CLI `mgc` da Magalu Cloud, permitindo que os usuários utilizem esta ferramenta sem precisar instalá-la diretamente em seus hosts. Utilizando a imagem Docker, você pode executar o `mgc` em qualquer sistema que suporte Docker, garantindo portabilidade e isolamento.


## Pré-requisitos

Antes de começar, certifique-se de que você tem o Docker instalado e funcionando em sua máquina. Visite [Docker](https://www.docker.com/get-started) para instruções de instalação.


## Facility 

Para facilitar, você pode utilizar diretamente a imagem não oficial `caiomarcatti12/magalu-cloud-cli:0.0.1` disponível no Docker Hub, sem a necessidade de construir a sua própria imagem.

```bash
docker run --rm --name magalu-cloud-cli -p 8095:8095 -it caiomarcatti12/magalu-cloud-cli:0.0.1
```

Este comando irá realizar o pull da imagem para seu ambiente e em seguida inicializar o terminal do container no modo interativo para que possa ser utilizado

## Construindo a Imagem Docker

Se desejar construir sua própria imagem Docker, você precisará de um arquivo `Dockerfile` contido nesse repositório. Após ter o `Dockerfile` como discutido anteriormente, você pode construir a imagem com o seguinte comando:

```bash
docker build -t mgc-cli .
```

Este comando cria uma imagem Docker chamada `mgc-cli` com base no `Dockerfile` no diretório atual.

### Executando o Terminal do Container de Modo Interativo

Para interagir com o `mgc` CLI de forma interativa, você pode iniciar o container no modo terminal:

```bash
docker run --rm -it mgc-cli
```

Este comando abre um shell dentro do container, onde você pode executar os comandos `mgc` diretamente.

## Utilizando os Comandos

A partir deste ponto, você pode utilizar todos os comandos disponíveis na [documentação oficial do `mgc`](https://docs.magalu.cloud/docs/cli-mgc/overview) da Magalu Cloud. Isso inclui comandos para gerenciar serviços, configurar recursos e muito mais.

## Conclusão

Usar o mgc CLI dentro de um container Docker não apenas oferece um ambiente isolado e portátil para gerenciar suas operações na Magalu Cloud, como também aumenta a segurança. Ao encapsular o CLI em um container Docker, você evita armazenar as credenciais diretamente nos hosts, reduzindo o risco de exposição de dados sensíveis. Esse método de isolamento garante que as informações críticas sejam mantidas em um ambiente controlado e seguro, ideal para operações que necessitam de alto nível de confidencialidade e integridade. Portanto, essa abordagem é fundamental para garantir que suas configurações de host não interfiram com as operações da CLI e protejam seus dados de acessos não autorizados.

Este exemplo prático destaca como as práticas de segurança e a tecnologia de containers podem ser utilizadas para proteger eficazmente suas ferramentas e dados no ambiente de cloud.