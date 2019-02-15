---
layout: post
title: Tomada de decisão
author: Achilles
---
As aulas voltaram meus amigos, vou começar ou tentar postar alguns trechos de códigos relacionados as aulas na FIAP. Qualquer coisa estamos ai.

Tomada de decisão, de forma clara: o programa vai tomar um decisão a partir de um dado que ele receber. Eu vou mostrar um exemplo prático escrito em python:

{% highlight python %}
x = int(input('Escreva um número de 0 à 10: '))
# Variável X que recebe um valor do tipo inteiro do usuário
if x <= 5:
# Se o número contido dentro da variável X, que foi posta
# pelo usuário for menor (<) ou igual (=) a 5, execute a
# próxima linha.
    print('Você escolheu um número igual ou menor que 5')
# Impressão contida dentro da condição if se essa for
# True (verdade).
else:
# else (se não), se o valor da condição if for False (falsa),
# elese passa a ser a codição em execução e ele irá executar
# as instruções que nele estão contido
    print('Seu número é maior de 5')
# Impressão copntida dentro de else
{% endhighlight %}

###### Código sem comentários
{% highlight python %}
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
x = int(input('Escreva um número de 0 à 10: '))
if x <= 5:
    print('Você escolheu um número igual ou menor que 5')
else:
    print('Seu número é maior de 5')
{% endhighlight %}

Veja que em python também é simples entender o código e assim como em pseudocódigo, python é claro no que ele mostra. Essa estrutura acima é simples e já joguei um else por que acho que ninguém usa só if. Vou mostrar mais dois códigos, mas sem comentários, estes veem logo abaixo.

###### Tá com fome?
{% highlight python %}
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
decisao = str(input('Escreva S se você está com fome ou escreva N se você não quer comer: '))
if decisao==S or decisao==s:
    print('Eu tenho Toddynho e Trakinas, se você quiser!')
else:
    if decisao==N or decisao==n:
        print('Beleza, se você ficar com fome me avisa!')
    else:
        print('Você precisa digitar S ou N para que eu saiba se você tem fome. Tente de novo.')
{% endhighlight %}

###### Empréstimo bancário
{% highlight python %}
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
casa = float(input('Qual o valor da casa R$'))
salario = float(input('Qual seu salário R$'))
anos = int(input('Em quantos anos você pretende pagar? '))
divd = casa / (anos * 12)
mini = salario * 30 / 100
if divd <= mini:
    print('Empréstimo aprovado!')
else:
    print('Emprestimo reprovado.')
    print('Não é possível liberar empréstimo com base em seu salario de R${:.2f}'.format(salario))
    print('Pois sua dívida seria superior a 30% de seu salário e sua dívida seria de R${:.2f}'.format(divd))
{% endhighlight %}

Perceba que nos três exemplos houve um input (inserção) de dados por parte do usuário, no código `ta_com_fome.py` foi solicitado um carácter, 'S' ou 'N', para que o programa pudesse tomar uma decisão com base na resposta do usuário. No `emprestimo_bancário.py` a mesma coisa ocorreu, mas, aqui foi solicitado valores númericos e a partir dai o programa também irá tomar uma decisão.

|`float: ponto flutuante`|||`Exemplo: 5.5`|
|`int: númeiro inteiro  `|||`Exemplo: 1`|

Veja que houve um volume alto no uso de variáveis e nesses exemplos poderia ter usado menos, mas para entender o que tá rolando, o uso de variáveis é útil para saber em que pé estamos e o que o programa está fazendo. Também utilizei comparadores (== e <=) para que o programa valide se a informação é verdadeira, do contrário, será falsa.

|`Comparador de igualdade : ==`|
|`Comparador menor ou igual : <=`|
|`Comparador ou: or`|

Execute os programas e veja output. O próximo exemplo foi feito pelo professor em pseudocódigo e resulta na informação com base na massa corporal do usuário.

###### Índice de massa corporal
{% highlight python %}
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
m = float(input('Seu peso atual: ')) # exemplo: 72.8
h = float(input('Sua altura: ')) # exemplo 1.80
imc = m / (h * h)

if imc < 18.5:
	print('Sua massa corporal é de: {:.2f}'.format(imc))
	print('Peso abaixo')
elif imc >= 18.5 and imc <= 24.9:
	print('Sua massa corporal é de: {:.2f}'.format(imc))
	print('Peso normal')
elif imc >= 20 and imc <= 29.9:
	print('Sua massa corporal é de: {:.2f}'.format(imc))
	print('Sobrepeso')
elif imc >= 30 and imc <= 34.9:
	print('Sua massa corporal é de: {:.2f}'.format(imc))
	print('Obesidade (Grau I)')
elif imc >= 35 and imc <= 39.9:
	print('Sua massa corporal é de: {:.2f}'.format(imc))
	print('Obesidade severa (Grau II)')
elif imc > 40:
	print('Sua massa corporal é de: {:.2f}'.format(imc))
	print('Obesidade Mórbida (Grau III)')
else:
	print('Valor não encontrado!')
{% endhighlight %}

|`Comparador maior que:        >`|
|`Comparador menor que:       <`|
|`Comparador maior ou igual: >=`|
|`Comparador 'e': and`|

Nesse exemplo acima ao invés de usar vários if's dentro de um else e com o perigo do código ficar gigantesco, usei o chamado elif (else + if = elif == se não se) , que também irá checar se determinada expressão é verdadeira, do contrário o programa irá pular para o else.

Note que else não recebe nenhum objeto para checar, já que o mesmo não precisa e não consegue realizar o processo. Uma vez que else só será executado se todas as informações anteriores forem falsas, não faria nenhum sentido haver um comparador nele.

Bom, creio que com estes exemplos o colega que teve ou tinha dúvidas, ficou com mais algumas (ou não), se esse for o caso, fique a vontade pra me chamar no grupo ou pode me chamar por algum meio de comunicação intergálatico. See you next.
#Show_Me_The_Code.

`Os códigos apresentados foram codados para Python 3.x, salva exceções que podem ser executadas em python 2.x`.

`Os 'comparadores' >, <, <=, >= e ==, são conhecidos como Operadores Relacionais e no caso do 'and' e 'or', são Operadores Lógicos`.
