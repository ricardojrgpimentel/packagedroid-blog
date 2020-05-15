---
title: Projeto Splitstreamsite
date: 2019-12-28
description: O SplitStream nasceu da necessidade de poder assistir a duas ou mais streams ao mesmo tempo.
tags: 
  - projeto
  - splitstream
categories: 
 - projeto
thumbnail: /2019/12/28/projeto-splitstreamsite/ogimage.png
---

O SplitStream nasceu da necessidade de poder assistir a duas ou mais streams ao mesmo tempo.

Visto que, grande parte das plataformas existentes requerem a introdução do ***username***, decidi utilizar a API, disponibilizada pela própria Twitch, para criar uma interface similar à existente, no site da Twitch.

<!-- more -->

![splitstream](8BDcCl5.jpg)

Com isto a exploração por jogos e streamers torna-se muito mais fácil e simples.

A oportunidade de incluir vários streamers ao mesmo tempo pode tornar-se um pouco confuso, visto que o chat e video são dois grandes focos de atenção.

De forma a tornar o projeto mais versátil, decidi incluir uma opção que oferece ao utilizador a liberdade de assistir a uma(s) stream(s) em 3 modos:

* Video e Chat
* Video
* Chat

### Video e Chat

![video-chat1](SAwuEgr.jpg)

### Video

![video-chat2](400lvXw.jpg)

### Chat

![video-chat3](CGMpAQ2.jpg)

Para além destas opções, é ainda possível partilhar facilmente qualquer visualização.

A partir do **URL** da página, para cada stream selecionada, é criada uma query string da seguinte forma:

```bash
?streamBox1=HighDistortion&streamBox2=SilverName&streamBox3=TimTheTatman&streamBox4=AdmiralBulldog
```

## Para fechar

Espero que seja de alguma forma útil, para quem utilizar, dúvidas e sugestões são sempre bem-vindas.

[SplitStream.site](https://splitstream.site/)