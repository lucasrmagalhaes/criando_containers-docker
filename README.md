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

Ganhamos:
Melhor controle sobre o uso de cada recurso (CPU, Disco, Rede... etc) <br>
Agilidade na hora de criar ou remover um container <br>
Maior facilidade na hora de trabalhar com diferentes versões de linguagens e bibliotecas <br>
Mais leves que as VM