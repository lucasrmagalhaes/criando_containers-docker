**Docker:** Criando containers sem dor de cabeça.

A evolução do host de aplicações <br>
Antigamente... Várias aplicações, vários servidores. <br>
Capacidade pouco aproveitada. <br>
Muito tempo ocioso! <br>
Muitos recursos desperdiçados!

Melhorando a situação: Virtualização <br>
APP - VM -> Hypervisor -> S.O. (Um Sistema Operacional para cada VM) -> Hardware

Nem tudo são flores... o problema das VMs. <br>
Quanto mais VMs, mais custos de hardware - processamento, configuração, atualização, segurança e tempo.

Então como melhorar agora? A era dos containers! <br>
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

Docker Engine: Tecnologia mais famosa e responsável por fazer o meio de campo entre os containers e o SO. <br>
Docker Compose: Um jeito fácil de definir e orquestrar múltiplos containers. <br>
Docker Swarm: Uma ferramenta para colocar múltiplos Dockers Host's para trabalharem juntos em cluster. <br>
Docker Hub: Um repositório com mais de 250 mil imagens diferentes para os seus containers. <br>
Docker Machine: Uma ferramenta que nos permite instalar e configurar em host virtuais.

```
docker version
```

```
docker run hello-world
```

[Play With Docker](https://labs.play-with-docker.com/)
Ao acessar o site basta clicar em +Add New Instance e começar a utilizá-lo como estivesse usando sua máquina normalmente.