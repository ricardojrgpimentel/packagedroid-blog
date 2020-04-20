---
title: Instalação do Youtube Vanced (root)
date: 2020-04-18 20:31:54
description: Instalação do Youtube Vanced (rooted) no Android 10 LineageOS 17.1
tags: 
  - android
  - magisk
categories: 
 - Android
 - Sistemas Operativos
cover: https://packagedroid.com/2020/04/18/instalacao-youtube-vanced/banner_youtube_vanced.png
---

O Youtube Vanced é uma versão do Youtube que permite utilizar vários recursos da versão Premium, entre eles a visualização sem interrupção para anúncios, visualização dos vídeos em segundo plano, com o ecrã bloqueado, etc...

Nesta publicação vamos instalar o Vanced no sistema Android 10 (LineageOS 17.1).

# Instalação

## Magisk

O Magisk é o utilitário que permite gerir quem tem acesso root no vosso smartphone, permite ainda instalar vários "modulos", que por sua vez utilização os recursos do Magisk para abilitar novas funcionalidades que, por norma, não estão disponiveis numa versão *vanilla* do sistema Android.

Para o nosso sistema, visto que a instalação da ROM em questão foi feita com recurso ao TWRP, o mesmo será feito com a instalação do Magisk.

No repositório [github](https://topjohnwu.github.io/Magisk/install.html) devem de fazer download da última versão disponível, após o download do ficheiro .zip, devem de copiar o mesmo para o vosso *smartphone* e reiniciar em modo de **recuperação (recovery mode)**

No modo de recuperação, neste caso o **TWRP** basta pressionar o botão **Install** 

![twrp1](twrp1.png)

em seguida selecionar o ficheiro .zip 

![twrp2](twrp2.png)

e deslizar para instalar
 
 ![twrp3](twrp3.png)

 Após a instalação basta reiniciar o *smartphone*, devem então de ter disponivel a aplicação **Magisk Manager**

 ![magisk1](magisk.png)

 ## EdXposed

 A aplicação **EdXposed** é a continuação do desenvolvimento da famosa aplicação **Xposed**, uma framework que permite modificar o comportamento de vários recursos do sistema, sem alterar ficheiros de origem.

 A instalação do EdXposed requer os seguintes modulos do Magisk:

 * Riru (Riru Core)
 * Riru EdXposed

 Devem de reiniciar o vosso *smartphone* após a instalação de ambos os modulos, de forma a ativar os mesmos, uma correta instalação e ativação resulta no seguinte ecrã:

![magisk2](magisk2.png)

Com isto vamos abrir a aplicação **EdXposed** e selecionar o separador *Canary*, aqui vamos pressionar o botão **Install/Update** que deverá de iniciar o *download* de um ficheiro **.zip**, este deve de ser instalado pelo **TWRP** da mesma forma que fizemos com o **Magisk**.

Após a instalação a aplicação deverá de apresentar a seguinte mensagem a azul:

![edxposed1](edxposed.png)

## CorePatch

O CorePatch permite desativar a verificação da *signature* na instalação de aplicações modificadas por terçeiros.

O repositório da aplicação encontra-se aqui [github](https://github.com/coderstory/CorePatch)

A instalação passa por fazer o *download* do ficheiro *.apk* correspondente ao vosso sistema e ativar o modulo no *EdXposed* (ambas as tarefas requerem reinicio do sistema)

* [CorePatch 2.0 (Android 4.4 ao 7)](https://mega.nz/file/cM1ShaiI#d8wO6wCurgiOWAPjAL1gJA52E9M-vNFEbuwSfkj_5SE)

* [CorePatch 2.2 (Android 7 ao 10)](https://mega.nz/file/dQ02DaLA#0Yjg40AHQOUxY7i_7ku5Q2zbGK1c2IH_DTCaXYzxWaE)

Com a aplicação instalada vamos então ativar as seguintes opções:

* Allow app downgrades
* Disable Package Manager Signature Verification

![corepatch1](corepatch.png)

## SAI

A aplicação SAI permite criar e instalar pacotes com vários ficheiros *.apk*, visto que as novas versões do **Vanced** encontram-se neste formato.

A instalação é feita diretamente da **Play Store**: [Split APKs Installer (SAI)](https://play.google.com/store/apps/details?id=com.aefyr.sai&hl=en_US)

## Vanced

Agora que temos todos os recursos instalados, vamos então instalar o **Vanced**, para isso devem de aceder a [vanced.app](https://vanced.app/) e fazer download da versão *root* com o tema à vossa escolha.

De seguida basta abrir a aplicação SAI e selecionar o ficheiro *.apks* obtido no passo a cima, a instalação resultará no seguinte ecrã:

![sai1](sai.png)

Com isto o **Vanced** encontra-se agora instalado no vosso sistema.
