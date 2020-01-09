---
title: mac OS Catalina no VirtualBox
date: 2019-11-05 09:46:54
tags: 
  - macOS
  - virtualbox
categories: 
 - Tutorial
 - Sistemas Operativos
cover: https://packagedroid.com/2019/11/05/macOS-Catalina-no-VirtualBox/vm17.jpg
---

A utilização do sistema operativo MacOS encontra-se limitado apenas às máquinas certificadas da Apple.
Isto faz com que seja quase impossivel testar o mesmo sem comprar um computador Apple.
Este tutorial tem como finalidade possibilitar o teste do sistema operativo MacOS no virtualbox.
A instalação do MacOS no virtualbox é um pouco diferente do habitual, no que toca a instalação de sistemas operativos no virtualbox.

De forma muito resumida, o [Virtualbox](https://www.virtualbox.org/) permite executar máquinas virtuais no vosso computador.
Um pouco como um pc dentro de outro pc

![inception](inception.jpg)

## Configuração do VirtualBox

A configuração da máquina virtual passa pelos seguintes passos:

* Criação da máquina virtual

A criação da máquina virtual é igual a qualquer outra.
Se já utilizaram o VirtualBox estes passos serão bastante familiares

### Nome da Máquina Virtual
Utilizem o mesmo nome que se encontra na imagem, pois será usado posteriormente noutros passos.

![vm1](vm1.jpg)

### Ram disponivel na máquina virtual
![vm2](vm2.jpg)
### Criação do tipo de armazenamento virtual
![vm3](vm3.jpg)

![vm4](vm4.jpg)

![vm5](vm5.jpg)

![vm6](vm6.jpg)

### Definições adicionais da máquina virtual
Com a máquina criada, vamos alterar algumas definições da mesma.
Certifiquem-se se as vossas definições são iguais às seguintes:

![vm7](vm7.jpg)

Devem de ter em conta o vosso processador, neste caso o meu apresenta 8 cores disponiveis, e decidi usar 2 cores para a máquina.
Quanto mais cores alocarem à máquina melhor será a performance.
![vm8](vm8.jpg)

![vm9](vm9.jpg)

![vm10](vm10.jpg)

No separador **Storage** vamos adicionar o ficheiro .iso do MacOS.
A criação do mesmo não será apresentada neste tutorial, podem obter o mesmo por aqui:

base64
```shell
aHR0cHM6Ly93d3cuZ2Vla3Jhci5jb20vZG93bmxvYWQtbWFjb3MtY2F0YWxpbmEtaXNvLWZvci12bXdhcmUtdmlydHVhbGJveC8=
```

![vm11](vm11.jpg)

Com o ficheiro .iso pronto, precisamos agora de adicionar um novo disco virtual à máquina virtual.
Para isso precisam de fazer download do disco aqui:

base64
```shell
aHR0cHM6Ly9kcml2ZS5nb29nbGUuY29tL2ZpbGUvZC8xSnZUdmFab0Nxajc0eHVjYm5xVG9XeUVWbWpTNzNGU2Qvdmlldz91c3A9c2hhcmluZw==
```

Com o download feito vamos adicionar o disco da seguinte forma:

![vm12](vm12.jpg)

Escolhemos a opção **Choose existing disk**
![vm13](vm13.jpg)

E adicionamos o disco
![vm14](vm14.jpg)

Com o disco configurado vamos passar aos comandos 

![hackerman](hackerman.png)

### Comandos

Vamos então abrir a linha de comandos e digitar os seguintes comandos:

Devem de introduzir cada linha seguido de **Enter**

Cada comando não deverá de retornar nada, se por alguma razão for apresentado algum erro, certifiquem-se que o caminho da instalação do VirtualBox corresponde ao apresentado no primeiro comando

```shell
cd "C:\Program Files\Oracle\VirtualBox"
.\VBoxManage.exe modifyvm "macOS Catalina" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
.\VBoxManage.exe setextradata "macOS Catalina" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
.\VBoxManage.exe setextradata "macOS Catalina" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
.\VBoxManage.exe setextradata "macOS Catalina" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
.\VBoxManage.exe setextradata "macOS Catalina" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
.\VBoxManage.exe setextradata "macOS Catalina" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
```

## Instalação do MacOS Catalina

Com todos os passos executados vamos então iniciar a máquina e proceder à instalação do MacOS.
Com a máquina ligada devem de aguardar alguns minutos até ser apresentada a primeira interface gráfica:

![vm15](vm15.jpg)

Começamos por preparar o disco, para isso selecionamos a opção **Utilitário de discos** e formatamos o disco com as seguintes opções:

![vm16](vm16.jpg)

Com o disco formatado, basta fechar o **Utilitário de discos** e proceder à instalação do MacOS, selecionando a opção **Instalar o macOS**.
A instalação é bastante simples, e cabe a cada um decidir a configuração do mesmo até chegarem a este ecrã:

![vm17](vm17.jpg)

### Passos finais da instalação

No fim da instalação a máquina irá reiniciar, nesse momento devem de fechar o VirtualBox, pois é preciso realizar mais alguns passos.
Nas definições da máquina devem de remover o *.iso* de instalação, para que a máquina não faça *boot* novamente da instalação.

![vm18](vm18.jpg)

De seguida devem de inicar a máquina e no momento do *boot* devem de pressionar a tecla **ESC** até ser apresentado o seguinte ecrã:

![vm19](vm19.jpg)

Neste ecrã vamos digitar o seguinte comando:

```shell
install.nsh
```

Este comando irá finalizar a instalação do sistema operativo e concluir o tutorial

![finally](finally.jpg)

Neste momento encontra-se configurada a máquina virtual com MacOS no VirtualBox