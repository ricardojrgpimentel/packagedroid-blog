---
title: Setup Ambiente de Desenvolvimento em Windows
date: 2020-03-30
description: Configuração do Windows para desenvolvimento com as principais ferramentas de produção
tags: 
  - windows
  - setup
categories: 
 - Windows
 - Sistemas Operativos
thumbnail: /2020/03/30/windows-setup-ambiente-desenvolvimento/banner_windows_ambiente_dev.png
---

# Introdução

A configuração aqui documentada varia consoante as vossas necessidades, contudo, penso que a mesma abrange um grande número de *use cases*.

<!-- more -->

A principal utilização do Windows, no meu dia-a-dia, gira à volta do desenvolvimento web. Com isto a configuração aqui documentada está focada nas seguintes necessidades:

* Facilitar a instalação de ferramentas de produtividade
* Manter todo o ecossistema atualizado
* Importar e exportar as definições das diversas ferramentas

# Software

## Scoop

O Scoop é um utilitário que permite instalar software no vosso computador muito ao estilo unix. A partir da linha de comandos é possivel procurar, instalar e atualizar uma grande variedade de softwares.

A instalação é muito simples, como podem verificar no website do mesmo: [scoop](https://scoop.sh/), basta executar o seguinte comando:

```bash
iwr -useb get.scoop.sh | iex
```

Com o scoop no sistema, a instalação do seguinte software torna-se muito mais fácil.

A gestão do scoop é feita da seguinte forma:

```bash
# Atualiza o Scoop
scoop update

# Atualiza uma aplicação especifica
scoop update vscode

# Atualiza todas as aplicações
scoop update *

# Procurar por aplicações
scoop search vscode

# Mais opções
scoop help
```

## Git

O Git é indispensável para qualquer desenvolvedor, grande parte do software existente vive nalgum repositório, onde a gestão do mesmo é feita com git.

A instalação é simplesmente:

```bash
scoop install git
```

Apesar de não ser necessário para o funcionamento do git, sugiro instalarem o *posh-git*:

```bash
scoop install posh-git
```

O posh-git é uma integração das funcionalidades do git no powershell, de forma termos acesso a uma maior número de informações.

A instalação do scoop não está completa sem o acesso aos seguintes buckets:

```bash
scoop bucket add extras
scoop bucket add versions
```

## Cmder

A linha de comandos do Windows é limitada no número de funcionalidades bem como na personalização, este problema é facilmente contornado com o Cmder.

A instalação é feita com o seguinte comando:

```bash
scoop install cmder
```

Como podem ver, a criação desta publicação foi feita com a ajuda do Cmder

![cmder](cmder.png)

A minha configuração: [gist](https://gist.github.com/ricardojrgpimentel/5c1a3b835483135021237803e1b7c82f)

## Terminus

Em alternativa ao Cmder existe o Terminus.

A instalação é feita da seguinte forma:

```bash
scoop install terminus
```

O terminus permite utilizar a configuração do Cmder no *profile* da aplicação.

## Visual Studio Code

O meu editor principal é o Visual Studio Code, existem muitos outros, que podem ser instalados facilmente com o scoop.

A instalação do mesmo é feita da seguinte forma:

```bash
scoop install vscode
```

A minha configuração do visual studio code [gist](https://gist.github.com/ricardojrgpimentel/4ed74dd2d67c984a4faa57809a1f1bfa)

## SSH

Por defeito o cliente SSH já se encontra ativo, caso tenham dificuldades a adicionar uma nova key, verifiquem o estado do *ssh-agent*:

```bash
Get-Service ssh-agent
```

Caso o *Status code* seja **Stopped** devem de executar os seguintes comandos:

```bash
# Altera o estado do serviço
Set-Service -Name ssh-agent -StartupType Manual

# Inicia o serviço
Start-Service ssh-agent
```

# Resumo
Tendo em conta as minhas necessidades, estes são os principais passos a tomar, na configuração do Windows, relembrando que podem ou não ter os mesmos requisitos para o vosso ambiente de desenvolvimento.