---
layout: post
title: "Programming Python in Atom"
author: Achilles
---

Há um tempo eu venho utilizando o Atom como minha principal interface pra programação, ela é bem boa na verdade, eu tinha centro preconceito, mas eu decidi usar e ver qual é. Acabei me surpreendendo com a quantidade de pacotes que ela possui (about python of course).

Eu utilizo muito o Pycharm e junto dele o Kite, acabei vendo que o Atom tem suporte ao Kite também e isso foi um dos motivos que me fez testa-lo também. Mas chega desse enchimento de linguiça, como instala essa parada no Linux, Windows e MAC?

No Windows é simples e facinho, baixando o pacote de instalação no próprio site, e dá dois cliques, só, ele instala sozinho no diretório do usuário na pasta C:\Users\Achilles\AppData\Local\atom. No Linux também não tem segredo, se você usar uma distribuição Debian, Ubuntu ou variante, baixa o pacote .deb e seja feliz seguindo as instruções abaixo.
```shell
~ $ wget -qO – https://packagecloud.io/AtomEditor/atom/gpgkey | sudo apt-key add –
~ $ sudo sh -c ‘echo “deb [arch=amd64]https://packagecloud.io/AtomEditor/atom/any/ any main” > /etc/apt/sources.list.d/atom.list’
~ $ sudo apt-get update
```
Ocorreu tudo certo? Geralmente, isso é particular meu, eu saio da sessão atual ou reinicio a maquina e entro novamente pra dai instalar o pacote, mas, faz do seu jeito que dá certo também.

```shell
~ $ sudo apt-get install atom # Install Atom
~ $ sudo apt-get install atom-beta # Install Atom Beta
```

Caso você baixe o pacote, instala a partir do pacote!

```shell
~ $ sudo dpkg -i atom-amd64.deb # Install Atom
~ $ sudo apt-get -f install # Install Atom’s dependencies if they are missing
```

Se liga, é possível instalar o Atom em outras distros, CentOs, Red Hat, Fedora, todas essas que usam o gerenciador de instação YUM ou DNF, mas eu não vou jogar aqui, da uma olhada no link abaixo que você consegue Dewey.

[Atom][atom]

[Documentação][documents]

[atom]: https://atom.io
[documents]: https://flight-manual.atom.io/getting-started/sections/installing-atom
