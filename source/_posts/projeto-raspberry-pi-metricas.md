---
title: Projeto Raspberry Pi - Métricas de Desempenho
date: 2020-02-24 13:27:05
tags: 
  - raspberry
  - metricas
categories: 
  - Tutorial
  - Raspberry Pi
cover: https://packagedroid.com/2020/02/24/projeto-raspberry-pi-metricas/dashboard_final.png
---

# DASHBOARD
![Resultado Final](dashboard_final.png)

Este projeto tem como finalidade apresentar uma interface com as principais métricas de desempenho do vosso computador.
Todo o software aqui indicado pode correr diretamente na máquina em questão, sem necessidade de um raspberry.
A utilização de um raspberry é apenas uma possivel solução, de forma a apresentar a interface no interior do computador.

# AVISO

Este projeto encontra-se em desenvolvimento, as funcionalidades são limitadas e o processo de execução é longo.
O objetivo final passa por ser apenas necessário executar um único utilitário que resultará na apresentação da dashboard, até lá este é o processo necessário para exibir a mesma.

# Hardware

O hardware usado neste projeto é o seguinte:

* Computador com gráfica compativel com o MSI Afterburner
* Raspberry pi 3 B+ 1GB
* Monitor 4"

Esta é uma possivel solução, pois tudo depende das necessidades de software usadas neste projeto.

# Software

O software varia consoante o vosso setup, os requisitos minimos para correr a interface são:

* Navegador Web Chrome/Firefox/Edge
* NodeJS >= 8.10 
* npm >= 5.6
* MSI Afterburner
* MSI Afterburner Remote Server

Em algumas situações o **.dll** que se faz acompanhar com o Remote Server não permite aceder à informação necessária, este **.dll** resolve o problema:
[MSIAfterburner.NET.dll](http://rivatuner.doomdealer.com/afterburner/MSIAfterburner.NET/1.1.1/MSIAfterburner.NET.dll)

## Instalação

### MSI Afterburner/Remote Server

O MSI Afterburner é o software responsável por disponibilizar as métricas de desempenho da máquina em que for instalado.
Apesar do nome, este software não se encontra limitado a qualquer hardware da MSI.

A instalação destes dois utilitários é bastante simples, ambos encontram-se disponíveis aqui: [MSI](https://www.msi.com/page/afterburner)

Devem de fazer download do **MSI Afterburner** e do **MSI Afterburner Remote Server**

![msi](msiafterburnersite.png)

### NodeJS - Windows

A instalação do NodeJs no Windows pode ser feita acedendo a [Nodejs.org](https://nodejs.org/en/), ambas as versões disponiveis para download são compatíveis com o nosso projeto, a versão **LTS** é a recomendada.

Caso tenham instalado no vosso sistema o *scoop*, podem instalar o NodeJs da seguinte forma:

```bash
scoop install nodejs
```

Ou recorrendo ao ***nvm***:

```bash
scoop install nvm
nvm install --lts
nvm use --lts
```

### NodeJS - Linux

Em sistemas Linux o comando de instalação deriva consoante a distro, em Ubuntu existe a seguinte solução:

```bash
curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install nodejs
```

### Git - Windows

Neste momento fazemos uso do git de forma a clonar o repositório com os ficheiros necessários.
A instalação no Windows pode ser feita, facilmente, instalando o software disponivel nesta página:
[git-scm.com](https://git-scm.com/download/win)

ou utilizando o **scoop**:

```bash
scoop install git
```

### Git - Linux

No Linux, como o qualquer outro software, o comando de instalação deriva consoante a distro, em Ubuntu é da seguinte forma:

```bash
sudo apt install git
```

### Dashboard de Métricas

A dashboard encontra-se disponivel no seguinte repositório: [Github](https://github.com/ricardojrgpimentel/raspberry-pc-metrics)

De forma a instalar a dashboard vamos correr os seguintes comandos na máquina onde será apresentada a dashboard.

Neste exemplo vamos clonar o repositório para a pasta Documentos do Windows:

```bash
cd Documents
git clone https://github.com/ricardojrgpimentel/raspberry-pc-metrics.git
```

Em seguida vamos entrar pasta do projeto e instalar as dependências necessárias:

```bash
cd raspberry-pc-metrics
npm install
```

no fim da instalação vamos à pasta **server** e instalamos as dependências do mesmo:

```bash
cd server
npm install
```

Com estes passos a dashboard encontra-se instalada com todo o software necessário.

# Configuração

Após a instalação de todo o software necessário, vamos então proceder à configuração do mesmo.

Começamos por iniciar o MSI Afterburner e o Remote Server na vossa máquina.
Devem de certificar-se que ambos os aplicativos se encontram a funcionar, para isso basta aceder à barra de tarefas do Windows, no canto inferior direito, onde são apresentados os seguintes ícones:

![area_tarefas](area_tarefas.png)

Em seguida vamos alterar a password do Remote Server, para isso basta fazer clique com botão direito do rato no ícone do Remove Server e aceder à opção **Security** e alterar a password para **12345**.
Por defeito a configuração do server do projeto está a usar a password **12345**, esta pode ser alterada mais tarde.

De forma a testar a configuração feita até aqui, vamos aceder ao seguinte endereço no vosso browser [localhost:82/mahm](http://localhost:82/mahm)

Na janela de basic auth usamos o seguinte login:

Utilizador: **MSIAfterburner**
Password: **12345**

Caso seja apresentado um documento **xml** com informação relativa ao vosso pc, a vossa configuração encontra-se a funcionar, caso contrário, uma das possiveis soluções passa por usar o ficheiro **.dll** alternativo, disponibilizado a cima.

### Iniciar a Dashboard

Na linha de comandos ou powershell executamos os seguintes comandos:

```bash
cd Documents/raspberry-pc-metrics
npm start
```
Esta ação inicia a dashboard no modo de desenvolvimento, abrindo o browser no endereço [localhost:3000](http://localhost:3000)

### Iniciar a API da Dashboard

Na linha de comandos ou powershell executamos os seguintes comandos:

```bash
cd Documents/raspberry-pc-metrics/server
node server.js
```

Esta ação é responsável por iniciar o servidor que responderá aos pedidos da dashboard.

O resultado será algo deste género:

![cmder](cmder.png)

# Dashboard

Ao seguirem os passos a cima, a dashboard encontra-se acessível no seguinte endereço: [localhost:3000](http://localhost:3000) com o seguinte aspecto:

![Empty Dashboard](dashboard_empty.png)

De forma a apresentar dados vamos abrir a sidebar, a partir do canto inferior direito.
Aqui encontram as opções de configuração da mesma, de forma a sabermos que informação podemos exibir, vamos começar por clicar em **Fetch**.
Será apresentada uma lista com todas as métricas do vosso computador, basta então selecionar quais as métricas a exibir.

O resultado será algo deste género:

![Dashboard](dashboard_final.png)

Dashboard a correr num raspberry:

![raspberry](raspberry.jpg)