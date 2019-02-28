---
layout: post
title: Hacking Access Machine
author: Achilles
---

Para não ficar muito parado, resolvi escrever sobre uma máquina maneira e com nível de resolução fácil/médio no HTB. Não vou mostrar o root user, apenas o usuário simples, que já te garante uns pontinhos e a base para pegar o root.

Quem conhece o Hack The Box sabe que pra ownar as máquinas, tem que quebrar um pouco a cabeça, mas depois você acaba desenrolando que nem vê o quanto percorreu. A máquina que vou demonstrar, se chama Access e eu confesso que apanhei pra pegar uma informação, que mais para frente vocês irão saber qual é.

Depois de baixar meu acesso VPN, realizei um levantamento de informações da máquina, páginas, server, essas coisas, que não vou por aqui, porque são irrelevantes para o propósito já que, não há nada além de uma página estática disponível e uma coisa a mais, que só o root pode acessar #ficaAdica.

Primeira coisa, vamos levantar as portas utilizando o Nmap com usuário root.

![Nmap](/images/nmap.png)

Nesse scan parcial, já vi que tem três portas e duas delas muito me interessam, que são: telnet (23) e ftp (21). Deixei rolando o scan e só veio a confirmação dos serviços, se liga:

![Nmap 2](/images/nmap-2.png)

Primeiro vou dar uma olhada no FTP, mas porquê? Geralmente é comum em CTF ou máquinas desse tipo terem liberado o acesso anônimo, por isso vamos testar e ver qualé.

![FTP_anonimo](/images/ftp-1.png)

Ta permitindo acesso anônimo e agora a gente precisa checar se existem diretórios e arquivos que a gente pode ler.

![FTP_listagem](/images/ftp-2.png)

Beleza, vimos que tem diretório e arquivos, agora a gente precisa copiar esses arquivos para o host, mas antes, uma olhada no print de baixo.

![FTP_ascii_to_bin](/images/ftp-ascii-bin.png)

Ta vendo que houve um report de atenção quanto a nossa cópia, dizendo que pode não ter copiado de forma correta? Isso ai ocorre por conta desse arquivo não estar em ascii mode, não ser um texto puro no caso, para resolver isso e já copiar todos os arquivos dos dois diretórios, é preciso que o "get realize" a cópia dos arquivos como binários (tudo é binário na real, mas você entendeu), vai a imagem full.

![FTP_full](/images/ftp-full.png)

Sacou ali que é só colocar bin, dar o enter e fazer a cópia? Beleza, essa é a parte fácil, agora a gente tem que ver o que são esses arquivos e trata-los. De cara a gente já vê que o Access Control.zip esta com senha e para crackear vai ser complicado, então vamos pela lógica procurar a senha no backup.mdb.

Eu particularmente nunca trabalhei com esse arquivo, então fui dar uma googlada como tratar isso aí. Tem uma ferramenta chamada mdbtools, se você esta com gnu/linux como eu, dá um apt install mdbtools para usa-lo.

![mdbtools](/images/mdbtools.png)

Li como usa-lo de forma que eu faça meu trampo sem perder muito tempo, primeiro a gente tem que ver as tabelas do arquivo, como se fosse um .sql mesmo.

![mdb-tables](/images/tables.png)

Como são muitas coisas, a gente tem que ser sagas e ligeiro, por pensar em sql, eu já dei um grep user para ver se tem alguma parada.

![gre_user](/images/tables-2.png)

Saca só, o primeiro se chama auth_user (autenticação de usuário), assim que eu vi esse cara, eu já sabia que era esse que eu tinha que ver primeiro.

![auth_user](/images/auth_user.png)

Beleza! Essa tabela já mostra o próximo passo, se liga que tem um usuário chamado "engineer" com senha e a gente pegou um arquivo zipado no diretório "Engineer" lá no ftp.

![unzip_Access](/images/unzipA.png)

A senha bateu e foi possível extrair esse arquivo pst, o que me leva a mais um problema, como vou abrir essa po$%@? Eu poderia jogar no Thunderbird, mas me daria um trabalho e gastaria um tempo valioso. Por isso resolvi de novo caçar um jeito de abrir esse arquivo pelo terminal e achei um programa chamado readpst, aliás, eu já conhecia, mas nunca havia fuçado ele. Pois, bem, como instala? apt install pst-utils.

Já vamos usa-lo e ver qual vai ser desse arquivo.

![extract_pst](/images/pst.png)

Ele dropou um arquivo chamado "2", que por ser um pst é um e-mail, agora vamos ver o que tem nele.

![cat_2](/images/usertel.png)

Show! Temos um usuário e senha que muito provavelmente é de um usuário telnet, já que pelo ftp não tem mais nada (testei :p).

![Security_owned](/images/owned-user.png)

Isso aí, funfou legal e já temos a primeira flag que é a hash no final. Agora fica aí o desafio de continuar a pegar o root e ownar a máquina de fato. That's it, see you.
