---
title: Limpeza e Optimização do Windows
date: 2020-01-14 16:29:30
tags: 
  - windows
categories: 
 - Sistemas Operativos
cover: https://packagedroid.com/2020/01/14/limpeza-e-optimizacao-do-windows-limpeza-e-optimizacao-do-windows/windows10.jpg
---

A manutenção do Windows é um tópico importante para qualquer utilizador, visto que, esta tarefa é fundamental para manter a estabilidade de todo o sistema.
A utilidade desta publicação passa por demonstrar vários cuidados a ter com o vosso sistema, de forma a manter OS limpo, rápido e livre de problemas.

## Verificação do Disco

Existem vários utilitários para verificar a saúde do disco, alguns pagos e outros gratuitos.
Neste guia vamos usar o software disponibilizado pela Western Digital, que permite executar um diagnóstico ao vosso disco.
É importante verificar o estado do vosso disco, de forma a prevenir a perda de dados, resultante de uma falha de hardware.

![Western Digital](western-digital.jpg)

## Limpeza de ficheiros desnecessários

### Limpeza do Disco
A limpeza de ficheiros começa por correr periodicamente o utilitário "Limpeza do disco", facilmente acessivel pelo menu iniciar ou pesquisando pelo nome ```cleanmgr```.

Devem de realizar uma limpeza nos ficheiros do sistema, com especial atenção à seleção da pasta de Transferências, pois todos os ficheiros serão apagados.

![Limpeza do Disco](limpeza-disco.jpg)

### Cache de actualizações do Windows

A pasta SoftwareDistribution é responsável por manter a cache das atualizações do Windows, de forma a ser possivel apagar a pasta é necessário parar 2 serviços do Windows.
Para isso basta abrir o utilitário Serviços ou procurar por ```services.msc``` no menu Iniciar.
Na aplicação vamos procurar pelos seguintes serviços:

* Serviço de Transferência Inteligente em Segundo Plano
* Windows Update

Com a clique direito do rato vamos **parar** os serviços.
Agora basta aceder à pasta ```C:\Windows\SoftwareDistribution``` e apagar a mesma.
Os serviços voltam ao normal funcionamento depois de reiniciarem a máquina.

## Verificação por vírus/malware

### Segurança do Windows
A verificação por atividade malicosa pode ser feita de várias formas, com recurso a vários softwares.
A **Segurança do Windows** em grande parte dos casos, suficiente para manter o sistema protegido.
Devem de dar sempre especial atenção a alguma notificação do mesmo, caso exista a necessidade de proceder à execução de alguma tarefa por parte do utilizador.

No caso de estar tudo em ordem o painel é apresentado da seguinte forma:

![Segurança do Windows](seguranca-windows.jpg)

### Microsoft Safety Scanner

Este utilitário disponivel aqui: [Link](https://docs.microsoft.com/en-us/windows/security/threat-protection/intelligence/safety-scanner-download)

Permite realizar uma procura e limpeza rápida por qualquer ameaça existente, sem ser necessário instalar qualquer software.

### MalwareBytes

Esta empresa disponibiliza 2 softwares muito competentes no que toca à procura e limpeza de ameaças do sistema.

#### MalwareBytes Anti-Malware

A versão experimental gratuita é bastante boa, mas recomendo a desisntalação do mesmo após da execução da limpeza, de forma a evitar a constante notificação para a aquisição da versão paga.

#### MalwareBytes AdwCleaner

O AdwCleaner é ideal no que toca à limpeza daqueles problemas que afetam o vosso browser.
Por vezes a página inicial do browser é alterada, ou até mesmo o motor de busca é diferente, grande parte destes problemas resulta do acesso a websites maliciosos.
Com o AdwCleaner facilmente removem qualquer problema existente no vosso browser.

## Windows Updates
As actualizações do Windows são fundamentais para manter o sistema atualizado e protegido.
O Windows Update permite manter atualizado o sistema, mas também qualquer outro software fundamental ao funcionamento do sistema, como drivers e utilitários do sistema.

Devem de certificar-se que todas as atualizações encontram-se instaladas, ou verificar por possiveis erros na instalação das mesmas.
Caso tenham dado conta do assunto este deverá de ser o aspeto do mesmo:

![Windows Update](windows-update.jpg)

Tópico de discussão: [Forum](https://forum.packagedroid.com/t/limpeza-e-optimizacao-do-windows/15)