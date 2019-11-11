---
title: Bloquear anúncios com Raspberry Pi Zero e Pi-Hole
date: 2019-09-22 17:03:19
tags: 
  - raspberry
  - pi-hole
categories: 
  - Tutorial
  - Raspberry Pi
---

A finalidade desde projeto passa por bloquear, ao nível do DNS, os seguintes serviços web:

* Anúncios
* Redes de tracking (rastreamento do tipo: Google Analytics, Facebook pixel, etc...)
* Scripts de mining

No final da configuração será possivel adicionar outras opções de bloqueio, não estando limitado aos serviços acima descritos.

## Hardware

Para este guia vamos precisar do seguinte hardware:

* Raspberry Pi Zero
* Cartão micro SD >= 8GB
* Cabo de alimentação USB A <-> micro USB
* Cabo OTG
* Pen USB Wireless

![Raspberry](20190922_172207.jpg)

(Caso utilizem outro modelo de raspberry com wifi integrado não é necessário o cabo OTG nem a pen wireless)

Para a configuração inicial precisamos ainda de:

* Teclado USB
* Adaptador HDMI <-> mini HDMI
* Cabo HDMI
* Monitor

## Software

O software necessário passa por escolher uma versão de linux a usar no Raspberry, bem como um cliente de SSH para realizar a ligação ao mesmo.
Para este exemplo vamos usar o [Raspbian](https://www.raspberrypi.org/downloads/raspbian/)
No site da Raspberry têm acesso a um tutorial detalhado de como instalar o mesmo:
[https://www.raspberrypi.org/documentation/installation/installing-images/README.md](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)

## Configuração inicial

Na configuração inicial vamos ter de realizar os seguintes passos:

* Ligar o raspberry à rede WiFi
* Activar o serviço de SSH

Para este passo vamos utlizar o cabo HDMI, o teclado e o monitor

### Ligar o raspberry à rede WiFi

De forma a termos a certeza que o WiFi encontra-se a funcionar corretamente, vamos procurar pelas redes locais disponiveis com o seguinte comando:

```
sudo iwlist wlan0 scan | grep ESSID
```

Esta procura deverá de resultar numa lista de redes WiFi disponiveis com a nomenclatura **ESSID** seguido do nome da rede WiFi.
Na lista deverá de constar a vossa rede WiFi, devem de anotar o nome da mesma, no nosso caso o nome da rede é **NOS-EF32**
Em seguida vamos editar o ficheiro no qual será salvo os dados de ligação à rede WiFi:

```
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

Neste ficheiro vamos criar uma nova entrada com a seguinte estrutura:

```
network={
  ssid="NOS-EF32"
  psk="PALAVRA-PASSE_DA_REDE"
}
```

Para guardar basta usar o atalho **CTRL + X** depois **Y** e em seguida **ENTER**
Se tudo correr bem neste momento temos o nosso dispositivo pronto a ligar-se à rede WiFi, é possivel testar o mesmo com o comando ping:

```
ping -c 5 google.pt
```
O comando deverá de retorna 5 tentativas de ligação com o seguinte resultado:

```
64 bytes from mad07s09-in-f3.1e100.net (172.217.17.3): icmp_seq=1 ttl=55 time=24.9 ms
64 bytes from mad07s09-in-f3.1e100.net (172.217.17.3): icmp_seq=2 ttl=55 time=31.9 ms
64 bytes from mad07s09-in-f3.1e100.net (172.217.17.3): icmp_seq=3 ttl=55 time=30.6 ms
64 bytes from mad07s09-in-f3.1e100.net (172.217.17.3): icmp_seq=4 ttl=55 time=33.8 ms
64 bytes from mad07s09-in-f3.1e100.net (172.217.17.3): icmp_seq=5 ttl=55 time=30.0 ms
```

Desta forma o nosso dispositivo encontra-se ligado à internet via WiFi.

### Activar o serviço SSH

Para ativarmos o serviço SSH basta correr os seguintes comandos:

```
sudo systemctl enable ssh
sudo systemctl start ssh
```

## Instalação do Pi-Hole

O [Pi-Hole](https://pi-hole.net/) é um utilitário que permite bloquear, ao nível do DNS, vários serviços existentes na internet.
A principal funcionalidade passa por bloquear anúncios, trackers (Google Analytics, Facebook Pixel, etc) entre outros.

Dando continuidade ao não tutorial, neste ponto o vosso aparelho encontra-se pronto a funcionar apenas com o cabo de alimentação ligado, pois com o serviço SSH activo podemos realizar uma ligação ao mesmo sem ser preciso o uso de um monitor e cabo HDMI.

Para realizar a ligação ao Raspberry precisamos de um cliente SSH.
Existem vários clientes SSH para várias plataformas, neste tutorial vamos realizar a ligação ao Raspberry com 2 dispositivos distintos.
Vamos utlizar um computador com Windows 10 e um Smartphone com Android.

### Cliente SSH Windows 10

O Windows 10 dispõe de uma aplicação nativa que permite a ligação ao dispositivo via SSH.
Esta aplicação encontra-se ativa e pronta a usar na ultima versão do Windows 10 (1903). 
Para usar o cliente SSH basta abrir a PowerShell ou a linha de comandos e executar o seguinte comando:

```
ssh NOME_DE_UTILIZADOR@IP_DO_RASPBERRY
```

O **NOME_DE_UTILIZADOR** corresponde ao utilizador configurado no Raspberry, no momento de instalação do sistema operativo, no tutorial indicado o nome de utilizador é **pi** e a palavra-passe, por defeito, **raspberry**
O **IP_DO_RASPBERRY** corresponde ao IP da rede local atribuído ao Raspberry.
Este pode ser encontrado acedendo ao painel de controlo do vosso Router.

![Ip Router](2019-09-22_193743.jpg)

No nosso exemplo o ip do Raspberry é o **192.168.1.220**
Com esta informação vamos então realizar a ligação ao Raspberry:

```
ssh ip@192.168.1.220
```

Devem de introduzir a palavra-passe depois do comando acima.
O Raspberry irá mostra algo deste género:

![ssh-windows-10](2019-09-22_213302.jpg)

Neste momento estão prontos a executar comandos remotamente.

### Cliente SSH Android

Para o sistema Android vamos usar a aplicação **JuiceSSH** disponivel aqui:
[Google Play](https://play.google.com/store/apps/details?id=com.sonelli.juicessh&hl=pt_PT)

Depois de instalarem e iniciarem a aplicação vamos à opção **Conexões**, neste ecrá selecionamos a aba **Identidades** e adicionamos uma nova com as seguintes definições:

**Apelido:** Raspberry
**Usuário:** pi
**Senha:** raspberry (ou outra configurada na instalação do sistema)

Guardamos a identidade e voltamos à aba **Conexões** onde vamos adicionar uma nova com as seguintes definições:

**Tipo:** SSH
**Endereço:** 192.168.1.220
**Identidade:** Raspberry (referente ao apelido dado no passo anterior)

As restantes opções ficam com as predifinições existentes, basta guardar a nova conexão.
Caso tenham inserido todos os dados corretamente, ao selecionarem a nova conexão será apresentado o seguinte ecrã:

![JuiceSSH](Screenshot_20190922-214555_JuiceSSH.jpg)

Neste momento estão prontos a executar comandos remotamente.

### Instalação

Para a instalação do Pi-Hole basta correr o seguinte comando:

```
curl -sSL https://install.pi-hole.net | bash
```

Durante a instalação serão apresentadas algumas opções, estas podem ser alteradas se bem desejarem, no nosso exemplo vamos usar as seguintes:

* **Provedor de DNS:** Google DNS
* **Listas de Hosts:** Todas selecionadas
* **Protocolos:** IPv4, IPv6
* **Static Address:** Yes
* **Install web admin inteface:** On
* **Install web server:** On
* **Log Queries:** On
* **Privacy mode for FTL:** 0 Show everything

No fim da instalação será apresentado o seguinte ecrã:

![fim-instalacao](2019-09-22_220652.jpg)

Devem de anotar a palavra-passe para poderem aceder ao painel de controlo.

## Utlização do DNS

O Raspberry encontra-se a funcionar com o Pi-Hole a correr, mas para dar uso efetivo ao DNS e bloquear os anuncios, existem 2 opções:

* Usar o DNS ao nível do router
* User o DNS ao nivel do dispositivo a aceder à internet

Alguns routers não permitem a alteração do DNS, para isso devem de verificar no website do fabricante do vosso router se é possivel alterar o DNS do mesmo. 
O uso do DNS ao nivel do router permite aplicar o bloqueio a todos os dispositivos ligados à internet através do mesmo, poupando tempo a configurar cada aparelho individualmente para fazer uso do DNS do Pi-Hole.

### DNS Windows
No meu caso o router disponibilizado pela NOS não me permite alterar o DNS do router, assim sendo vou alterar o DNS do meu PC para usar o do Pi-Hole.

Nas propriedades da placa de rede do Windows é possivel alterar o DNS com as seguintes definições:

![ethernet-windows10](2019-09-22_221916.jpg)

No Servidor DNS preferido é usado o IP do Raspberry, no alternativo podem utilizar qualquer serviço de DNS, neste exemplo é usado o da Google.

### DNS Android

Nos aparelhos Android é possivel configurar o DNS em qualquer rede WiFi, 
Para isso devem de abrir as definições da rede em que se encontram ligados e alterar as **Definições IP** de **DHCP** para **Fixo**
Com esta opção ligada será apresentada a opção de alteração do DNS, como mostra a imagem:

![definicoes](Screenshot_20190922-222339_Settings.jpg)

O DNS 1 corresponde ao IP do Raspberry e o DNS 2 a outro serviço de DNS, neste exemplo é usado o da Google.



