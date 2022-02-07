**Docker:** Criando containers sem dor de cabeça.

**A evolução do host de aplicações** <br>
Antigamente... Várias aplicações, vários servidores. <br>
Capacidade pouco aproveitada. <br>
Muito tempo ocioso! <br>
Muitos recursos desperdiçados!

**Melhorando a situação: Virtualização** <br>
APP - VM -> Hypervisor -> S.O. (Um Sistema Operacional para cada VM) -> Hardware

**Nem tudo são flores... o problema das VMs.** <br>
Quanto mais VMs, mais custos de hardware - processamento, configuração, atualização, segurança e tempo.

**Então como melhorar agora? A era dos containers!** <br>
APP - Container - SO (Um Sistema Operacional para todos os containers) - Hardware <br>
Mais leve <br>
Não tem os custos de manter múltiplos S.O. <br>
Mais rápido de subir

**Ganhamos:** <br>
Melhor controle sobre o uso de cada recurso (CPU, Disco, Rede... etc) <br>
Agilidade na hora de criar ou remover um container <br>
Maior facilidade na hora de trabalhar com diferentes versões de linguagens e bibliotecas <br>
Mais leves que as VM

**Docker** <br>
Docker Inc. - A empresa <br>
Docker - A tecnologia de containers

Tecnologias de containers para prover ferramentas modernas para deployar e rodar aplicações.

**Docker Engine:** Tecnologia mais famosa e responsável por fazer o meio de campo entre os containers e o SO. <br>
**Docker Compose:** Um jeito fácil de definir e orquestrar múltiplos containers. <br>
**Docker Swarm:** Uma ferramenta para colocar múltiplos Dockers Host's para trabalharem juntos em cluster. <br>
**Docker Hub:** Um repositório com mais de 250 mil imagens diferentes para os seus containers. <br>
**Docker Machine:** Uma ferramenta que nos permite instalar e configurar em host virtuais.

Exibe a versão do docker.
```
docker version
```

Cria um container com a respectiva imagem passada como parâmetro.
```
docker run hello-world
```

[Play With Docker](https://labs.play-with-docker.com/) <br>
Basta clicar em +Add New Instance e começar a utilizá-lo como estivesse usando sua máquina normalmente.

```
docker run ubuntu
```

Lista todos os containers.
```
docker ps -a
```

```
docker run ubuntu echo "Olá Mundo"
```

Dentro do Container, consegue rodar comandos nativos da Imagem do Container.
```
docker run -it ubuntu
```

Lista só os containers ativos.
```
docker ps
```

exit ou Ctrl + d -> Sai do container.

Iniciar o container
```
docker start container_id
```

Parar o container
```
docker stop container_id
```

Acessar o container no modo interativo
```
docker start -a -i container_id
```

Remover um container
```
docker rm container_id
```

Remover containers inativos
```
docker container prune
```

Listar imagens
```
docker images
```

Remover imagem
```
docker rmi nome_imagem
```

Baixar uma imagem com a versão informada
```
docker run ubuntu:14.04
```

**Layered File System** <br>
Toda imagem que baixamos é composta de uma ou mais camadas. <br>
Essas camadas podem ser reaproveitadas em outras imagens, acelerando assim o tempo de download.

![Layer de Scrita](https://user-images.githubusercontent.com/43296467/152704905-91b18bb0-0ad7-4970-ab3e-9c32371f5aee.png)

Imagem não oficiais, criado por pessoas, informar o username/imagem
```
docker run dockersamples/static-site
```

-d -> detect, roda em background, liberando o terminal
```
docker run -d dockersamples/static-site
```

-t -> tempo, padrão é 10 segundos
```
docker stop -t 0 container_id
```

-P -> container atribui a porta aleatória
```
docker run -d -P dockersamples/static-site
```

Verificar a porta
```
docker port container_id
```

Definir um nome para o container
```
docker run -d -P --name meu-site dockersamples/static-site
```

Parar o container pelo o nome
```
docker stop -t 0 meu-site
```

Definir a porta que o container vai rodar - localhost:12345
```
docker run -d -p 12345:80 dockersamples/static-site
```

- e -> Variável de Ambiente
```
docker run -d -P -e AUTHOR="Lucas Magalhães" dockersamples/static-site
```

-q -> Retorna os IDs
```
docker ps -q
```

Para os containers com um comando só, útil para parar vários containers
```
docker stop -t 0 $(docker ps -q)
```

**Containers são voláteis:** Aonde salvar o código? Logs? Dados? Nos volumes! <br>
/var/www -> Docker Host

-v -> Especifica o caminho
```
docker run -v "/var/www" ubuntu
```

Informações do container
```
docker inspect container_id
```

Mounts -> Source -> Informa onde está salvando os dados localmente.

```
docker run -it -v "C:\Users\Lucas\Desktop:/var/www" ubuntu
```

```
cd var/www/
```

```
touch novo-arquivo.txt
```

```
echo "Este arquivo foi criado dentro de um volume" > novo-arquivo.txt
```

**Por que usamos volumes?** <br>
Muitas vezes removemos os containers após o uso. Volumes são usados para os dados que não devem ser removidos. <br>
É muito comum usar o container e apagá-lo após seu uso. Dessa forma também são removidos os dados desse container e aí entram os volumes que permitem salvar dados fora do container.

**Um volume fica salvo:** No Docker Host <br>
Fica salvo no computador onde a Docker Engine está rodando.


Informando o caminho e rodando o projeto - CAMINHO_HOST:CAMINHO_CONTAINER
```
docker run -d -p 8080:3000 -v "C:\Users\Lucas\Desktop\volume-exemplo:/var/www" -w "/var/www" node npm start
```

Dentro da pasta e rodando o projeto
```
docker run -d -p 8080:3000 -v "$(pwd):/var/www" -w "/var/www" node npm start
```

Build
```
docker build -f node.dockerfile -t lucasrmagalhaes/node .
```

Listando imagens
```
docker images
```

Remove e força o stop
```
docker rm -f container_id
```

Rodando a imagem criada
```
docker run -d -p 8080:3000 lucasrmagalhaes/node
```

Login do Docker HUB
```
docker login
```

Subindo a imagem
```
docker push lucasrmagalhaes/node
```

Baixando a imagem
```
docker pull lucasrmagalhaes/node
```

Verificar o ip da máquina
```
hostname -i
```

Ativando o comando ping no Ubuntu
```
apt-get update && apt-get install -y iputils-ping
```

Criando uma rede
```
docker network create --driver bridge minha-rede
```

Listando as redes
```
docker network ls
```

```
docker run -it --name meu-container-de-ubuntu --network minha-rede ubuntu
```

```
docker run -it --name meu-segundo-container-de-ubuntu --network minha-rede ubuntu
```

```
ping meu-container-de-ubuntu
```

```
docker pull douglasq/alura-books:cap05
```

```
docker pull mongo
```

Startando o mongo
```
docker run -d --name meu-mongo --network minha-rede mongo
```

Startando o projeto
```
docker run --network minha-rede --name alura-books -d -p 8080:3000 douglasq/alura-books:cap05
```

Salva os livros no banco
```
http://localhost:8080/seed
```

