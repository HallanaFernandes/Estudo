#  🐉 PYTHON

## 🟣 **TIPOS DE VARIÁVEIS**:
 
**NoneType e Type**

type = serve para identificar os tipos de variáveis

NoneType = tipo vazio

```python
telefone_fixo = None
print(telefone_fixo)
print(type(telefone_fixo))
```

**Numpéricas**

tipos de variáveis numéricas: Float (numero com virgula), int (numero inteiro) e complex

conversões de tipos numéricos:

```python
print(int(3.9))
print(float(10))
print(complex(1))
#me retorna:
#3
#10.0
#(1+0j)
```

```python
preco = 100
tipo_preco = type(preco)
print(preco)
print(tipo_preco)
# ---> me retorna 100
#<class 'int'>
```

**booleanos**
True e false

operadores lógicos:
> maior
< menor
== igual
>= maior ou igual
>= menor ou igual
!= diferente

and, or e not

and -----> o operador and retorna true se ambos os operadores forem verdadeiros, caso contrário, retorna fase

or   -----> o operador or retorna true se pelo menos um dos operandos for verdadeiro. retorna false somente se ambos os operadores forem falsos

not ----> o operador not inverte o valor do booleano

ORDEM = AND, OR E NOT

AND
```python
a = True
b = False
resultado = a and b
print(resultado)
# ---> FALSE
```
OR

```python
resultado_2 = a or b
print(resultado_2)
#---> TRUE
```
NOT

```python
c = True
resultado_3 = not c
print(resultado_3)
# --> FALSE
```

exemplo 1:

```python
codigo_de_seguranca = '852'
codigo_de_seguranca_cadastro = '010'
pode_efetuar_pagamento = codigo_de_seguranca == codigo_de_seguranca_cadastro
print(pode_efetuar_pagamento)
#me retorna false
```

exemplo 2:

```python
#ENCONTRE O VALOR DE X
a = False
b = True
c = False
x = not a and b or c
print(x)
#---> true
```
a and b —→ ele só retorna true caso os dois forem verdadeiro, neste caso retorna false

false or c —> ele retorna true caso um dos dois forem verdadeiro, neste caso retorna false, pois false + false = false 

not false = retorna true

**string**

***tamanho da string:***

```python
nome = 'hallana'
print(len(nome))
#--> 7
```

***concatenação:***

```python
nome = "hallana"
sobrenome = "fernandes"
nome_completo = f"olá meu nome é {nome} {sobrenome}"
print(nome_completo)
```

***fatiamento(slicing):***

```python
email = "hallana.fernandes@gmail.com"
print(email[0])
print("1:" + email[1])
#pega uma letra da palavra
#me retorna h e 1:a
#→ se eu colocar -1, ele me retorna o valor do ultimo elemento
```

***slicing por intervalo:***

```python
print(email[0:7])
#me retorna hallana
```

***métodos de strind***:
os métodos de string, não modificam a string original

```python
texto = 'abc'
texto_upper = texto.upper()  # Retorna uma nova string em maiúsculas
print(texto_upper)  # Imprime 'ABC'
print(texto)  # A string original 'abc' permanece inalterada

texto_stripped = texto.strip()  # Retorna uma nova string sem espaços em branco no início e no final
print(texto_stripped)  # Imprime 'abc' se não houver espaços em branco
print(texto)  # A string original 'abc' permanece inalterada
```

trabalhando com métodos de string:

```python
valor = 'ola'
print(valor.upper()) #vai deixar minha string maiuscula

ola_maiusculo = valor.upper() #atribuindo o valor maiusculo em uma nova variavel
print(ola_maiusculo) #vai deixar minha string maiuscula
```

trabalhando com mais de um método de string:
```python
	novo_valor = valor.upper().replace('parametr1', 'parametro2')
  print(novo_valor)

ou 

print(valor.upper().replace())
```

para saber aonde começa o índice da primeira palavra desejada (FIND):


```python
posicao = endereco.find('rj')
print(posicao)
#me retorna 4
# s - indice 0, p - indice 1, virgula - indice 2, espaço - indice 3, r - indice 4
```

conversão de string em numero e vice versa:

```python
numero_string = "123"
numero_inteiro = int(numero_string)
print(numero_inteiro)
#Isso converterá a string "123" para o número inteiro 123.
```

## 🟣 **OPERAÇÕES NUMÉRICAS**:

```python
#INCREMENTO
qtd_items_do_carrinho = 0
qtd_items_do_carrinho += 1

print(qtd_items_do_carrinho)

qtd_items_do_carrinho += 1
print(qtd_items_do_carrinho)
```

| DIA    | Total Vendas | Qtd Total Vendas | Ticket Médio |
|--------|--------------|------------------|--------------|
| 19/01  | a            | 3                | 320.52       |
| 20/01  | 834.47       | b                | 119.21       |
| 23/01  | 15378.12     | 5                | c            |


achando o resultado de A:

```python
qtd_vendida_19 = 3
ticket_medio_19 = 320.52
a = ticket_medio_19 * qtd_vendida_19
print(a)
```

achando o resultado de B:

```python
valor_total_20 = 834.47
ticket_medio_20 = 119.21
b = valor_total_20 / ticket_medio_20
resultado = f'o valor da quantidade vendida foi: {b}'
print(resultado)
```

achando o resultado de C:

```python
valor_total_23 = 15378.12
qnt_vendida_23 = 5
c = valor_total_23 / qnt_vendida_23
print(c)
```

função máximo e minimo 

```python
# COLOCAR NUMEROS EM ORDEM CRESCENTE
# Recebe os três números do usuário
num1 = float(input("Digite o primeiro número: "))
num2 = float(input("Digite o segundo número: "))
num3 = float(input("Digite o terceiro número: "))

# Encontra o menor número
menor = min(num1, num2, num3)

# Encontra o maior número
maior = max(num1, num2, num3)

# Calcula o número do meio
meio = (num1 + num2 + num3) - menor - maior

print(f"Números em ordem crescente: {menor}, {meio}, {maior}")
```

função SUM

```python
sum(list(range(1,10)))
#me retorna 45
```

## 🟣 **LISTAS, CONJUNTOS, DICIONÁRIOS E LISTAS DE DICIONÁRIOS**:

***listas***

**características das listas**

- **Ordenadas**: Os elementos em uma lista mantêm a ordem em que foram inseridos.

- **Mutáveis**: É possível alterar, adicionar e remover elementos da lista.

- **Elementos repetidos**: As listas podem conter elementos duplicados.

- **Sintaxe**: Os elementos são colocados entre colchetes **`[]`** e separados por vírgulas.

**uso** 

- Armazenamento de dados onde a ordem é importante.
- Quando a mesma informação pode aparecer mais de uma vez na estrutura.

- Útil quando a sequência e a posição dos itens são relevantes.

```python
lista_string = ['André Perez', 'andre.perez', 'andre123', 'andre.perez@gmail.com']
lista_numeros = [0, 1, 2, 3, 4]
a = 2
b = 1
c = 6
lista_variáveis = [a, b, c]
```

```python
#acessando um valor da lista por index, semelhante a string
nomes = ['ana', 'bianca']
nomes[0]
#---> ana 
```

***concatenação de lista***

```python
fabricantes_mobile_china = ['xiaomi', 'huawei']
fabricantes_mobile_eua = ['apple', 'motorola']
fabricantes_mobile = fabricantes_mobile_china + fabricantes_mobile_eua
```

***comprimento da lista***

```python
#LEN, semelhante a string
minha_lista = [10, 20, 30, 40, 50]
tamanho_lista = len(minha_lista)
print(tamanho_lista)
#me retorna --> 5
```

***atribuir um novo valor a lista***

```python
fabricantes_mobile[2] = 'nokia'
print(fabricantes_mobile)
#estou atribuindo na posição 2, o valor de nokia
```

***inserindo um novo valor em qualquer lugar da minha lista .insert()***

```python
juros = [0.05, 0.07, 0.02, 0.04, 0.08]
juros.insert(0, 0.10)
print(juros)
#---> [0.1, 0.05, 0.07, 0.02, 0.04, 0.08]
```
***inserindo um novo valor no final da minha lista .append()***

```python
juros.append(0.09)
print(juros)
#--> [0.1, 0.05, 0.07, 0.02, 0.04, 0.08, 0.09]
```

***removendo algum valor .remove()***

```python
juros.remove(0.1)
print(juros)
#---> [0.05, 0.07, 0.02, 0.04, 0.08, 0.09]
```

***removendo um valor pelo indice .pop()***

```python
juros.pop(2)
print(juros)
#--> [0.05, 0.07, 0.08, 0.09]
```

***conversão***

```python
email = 'andre.perez@gmail.com'
lista_email = list(email)

print(email)
print(lista_email)
#---> andre.perez@gmail.com
#['a', 'n', 'd', 'r', 'e', '.', 'p', 'e', 'r', 'e', 'z', '@', 'g', 'm', 'a', 'i', 'l', '.', 'c', 'o', 'm']
```

***sort - ordenara os itens da lista de forma crescente***

```python
lista_numeros = [30,10,10,5,15,20]
```

```python
lista_numeros.sort()
#[5, 10, 10, 15, 20, 30]
```

***count - retorna quantas vezes o item passado no parâmetro repete***

```python
lista_numeros.count(10)
#2
```

***extend - adiciona um lista no final da lista existente***

```python
lista_numeros.extend([3,1,0,5,2])
lista_numeros
#[10, 10, 15, 20, 40, 3, 1, 0, 5, 2]
```

***reverse - ordena os valores das listas de forma decrescente***

```python
lista_numeros.reverse()
#[2, 5, 0, 1, 3, 40, 20, 15, 10, 10]
```

***clear - remove todos os itens da lista***

```python
lista_numeros.clear()
lista_numeros
type(lista_numeros)
#list
```
**conjuntos**

listas que não permitem valores repetidos

obs: eu consigo adicionar e remover um novo elemento, entretanto não sei em qual ordem esse novo elemento irá ficar, e também não posso retribuir um novo valor

- **Não ordenados**: Os elementos não possuem uma ordem específica.

- **Mutáveis**: É possível adicionar ou remover elementos do conjunto, mas não é possível alterar um elemento específico, já que não possuem índices.

- **Elementos únicos**: Conjuntos não podem conter elementos duplicados. Se você tentar adicionar um elemento já existente, ele não será inserido novamente.

- **Sintaxe**: Os elementos são colocados entre chaves **`{}`**.

*Uso*:

- Remoção de duplicatas de uma sequência de elementos.

- Verificação de pertencimento de um elemento a um grupo sem se importar com a ordem.

- Realização de operações de conjuntos, como união, interseção e diferença.
    
Em resumo, as listas são mais adequadas quando a ordem e a duplicação importam, enquanto os conjuntos são mais úteis quando se trata de garantir elementos únicos e realizar operações de conjuntos de maneira eficiente.

```python
frutas = {'banana', 'maca', 'uva', 'uva'}
print(frutas)
#{'maca', 'uva', 'banana'}
#a ordem nao importa
#não permite valores repetidos
```

***operações com conjuntos***

```python
paises_1 = {'reino unido', 'suecia', 'russia', 'noruega', 'dinamarca'}
paises_2 = {'noruega', 'dinamarca', 'suecia'}
```

***pipe |***

```python
paises_3 = paises_1 | paises_2
#exclui os valores comuns
#{'dinamarca', 'reino unido', 'suecia', 'noruega', 'russia'}
```

***subtração -***

```python
paises_4 = paises_1 - paises_2
#ele diminui, o que tem em um conjunto que é semelhante ao outro conjunto, vai ser tirado fora, e vai sobrar os valores que são diferentes
#{'russia', 'reino unido'}
```

***métodos .add() e .remove()***

```python
#para adicionar e remover
variavel.add('valor')
variavel.remove('valor')
```

***conversão***

```python
times_paulistas = {'São Paulo', 'Palmeiras', 'Corinthians', 'Santos'}
print(times_paulistas)
print(type(times_paulistas))]

print(list(times_paulistas))
print(type(list(times_paulistas)))
#a forma mais facil de retirar duplicidade de listas seria transformando ela para um conjunto e depois transformar novamente para uma lista
```

***exemplo:***

```python
hashtags_seg = ['#tiago', '#joao', '#bbb']
hashtags_ter = ['#sarah', '#bbb', '#fiuk']
hashtags_qua = ['#gil', '#thelma', '#lourdes']
hashtags_qui = ['#rafa', '#fora', '#danilo']
hashtags_sex = ['#juliete', '#arthur', '#bbb']

hashtag_semana = hashtags_seg + hashtags_ter + hashtags_qua + hashtags_qui + hashtags_sex
print(hashtag_semana)
print(len(hashtag_semana))

set(hashtag_semana)

print(hashtag_semana)
print(len(hashtag_semana))
#---> ['#tiago', '#joao', '#bbb', '#sarah', '#bbb', '#fiuk', '#gil', '#thelma', '#lourdes', '#rafa', '#fora', '#danilo', '#juliete', '#arthur', '#bbb']
#15
#['#tiago', '#joao', '#bbb', '#sarah', '#bbb', '#fiuk', '#gil', '#thelma', '#lourdes', '#rafa', '#fora', '#danilo', '#juliete', '#arthur', '#bbb']
```

*dicionários*
os dicionários contem = chave: valor

```python
brasil = {'capital': 'brasilia', 'idioma': 'portugues', 'população': 210}
print(brasil)
```

***como acessar os valores das chaves***

os dicionários funcionam de maneira diferente das listas, não é mais utilizado [index] para acessar os valores, no caso o index de brasília seria capital e assim sucessivamente, ou seja para obter o valor de **brasilia**, acessamos pelo chave **capital.** a chave é o valor antes dos dois pontos e ela tem que ser sempre uma string.

```python
print(brasil['capital'])
#brasilia
```

***não é permitido chaves duplicadas***

```python
carro = {
    'marca': 'gol',
    'modelo': 'polo',
    'ano': 2021,
    'ano': 2023
}
print(carro)
#me retorna: {'marca': 'gol', 'modelo': 'polo', 'ano': 2023}
#ele reatribui o valor de 2021 para 2023
```

***podemos criar dicionários aninhados***

```python
cadastro = {
 'andre': {
 'nome': 'Andre Perez',
 'ano_nascimento': 1992,
 'pais': {
 'pai': {
 'nome': '<nome-do-pai> Perez',
 'ano_nascimento': 1971
 },
 'mae': {
 'nome': '<nome-da-mae> Perez',
 'ano_nascimento': 1973
 },
 }
 }
}
print(cadastro)
```

***para acessar o nascimento da mãe***

```python
cadastro['andre']['pais']['mae']['ano_nascimento']
#me retorna: 1973
```

***atribuir um novo valor***

```python
credito = {'123': 200, '154': 400}
credito['123'] = 300
```

***métodos .pop() ou .del()***

```python
credito.pop('154')
print(credito)

#ou

#del credito['154']
```

***manipulação de dicionários***

```python
produto = {'nome':'monitor',
           'valor':1200.00,
           'cor':'preto',
           'descrição':'29 polegadas'}
```

```python
print(produto.keys())  #vai me retornar as chaves
print(produto.values()) #vai me retornar os valores das chaves
print(produto.items()) #vai me retornar os dois
#dict_keys(['nome', 'valor', 'cor', 'descrição'])
#dict_values(['monitor', 1200.0, 'preto', '29 polegadas'])
#dict_items([('nome', 'monitor'), ('valor', 1200.0), ('cor', 'preto'), ('descrição', '29 polegadas')])
```

***iterando sobre os dicionários***

```python
for chave in produto.keys(): #quando eu quero iterar apenas sobre uma coisa, eu uso apenas um parametro CHAVE
  print(chave)
  #nome
  #valor
  #cor
  #descrição
```

```python
for chave, valor in produto.items(): #quando eu quero iterar sobre duas coisas, eu uso dois parametros, separados por virgula. CHAVE e VALOR
  print(chave)
  print(valor)
  print('----')
```

nome
monitor
-------
valor
1200
------
cor
preto
------
descrição
29 polegadas

***transformando os dicionários em uma lista de dicionários***

```python
produto1 = {'nome':'desktop',
           'valor':4800.00,
           'cor':'preto',
           'descrição':'computador da marca dell'}

produto2 = {'nome':'teclado',
           'valor':210.00,
           'cor':'preto',
           'descrição':'teclado mecânico ABNT2'}
estoque = [produto1,produto2]
estoque
```

*listas de dicionários*
com as listas, eu posso juntar vários dicionários

por ser uma lista ela é acessadas por index

```python
pessoa1 = {'nome': 'Alice', 'idade': 25, 'cidade': 'New York'}
pessoa2 = {'nome': 'Bob', 'idade': 30, 'cidade': 'San Francisco'}
```

```python
pessoas = [
    {'nome': 'Alice', 'idade': 25, 'cidade': 'New York'},
    {'nome': 'Bob', 'idade': 30, 'cidade': 'San Francisco'}
]
```
***como acessar uma lista de dicionários***

```python
pessoas = [
    {'nome': 'Alice', 'idade': 25, 'cidade': 'New York'},
    {'nome': 'Bob', 'idade': 30, 'cidade': 'San Francisco'}
]
#print(pessoas)
#print(pessoas[0]) #acessa a minha primeira linha de código, no caso: nome': 'Alice', 'idade': 25, 'cidade': 'New York'
#print(pessoas[1]) #acessa a minha segunda linha de codigo, no caso: 'nome': 'Bob', 'idade': 30, 'cidade': 'San Francisco'
#print(pessoas[0]['nome']) #acessa o nome da minha primeira linha, no caso: ALICE] LINHA E DEPOIS CHAVE
#Acessando o valor associado à chave 'nome' em ambos os dicionários --> FOR
for pessoa in pessoas:
    print(pessoa) #vai me retorna os dois dicionarios.
    print(pessoa['nome']) #acessando o NOME das pessoas, dos dois dicionarios
```

***Atividades***

```python
mercado_a = {'Sabão em Pó':17.80,
             'Detergente':2.00,
             'Arroz': 17.70,
             'Feijão':18.30,
             'Banana':2.50,
             'Danone':9.75,
             'Leite':6.60}

mercado_b = {'Sabão em Pó':16,
             'Detergente':3.52,
             'Arroz': 16.00,
             'Feijão':5.50,
             'Banana':2.20,
             'Danone':8.80,
             'Leite':7.00}

mercado_c = {'Sabão em Pó':15,
             'Detergente':3.50,
             'Arroz': 16.00,
             'Feijão':5.60,
             'Banana':2.30,
             'Danone':8.70,
             'Leite':5.50}             

lista_mercado = [mercado_a, mercado_b, mercado_c]
```

soma dos produtos do mercado A

```python
soma = 0
for item in mercado_a.values():
		soma = soma + item
		print(f'Item: {item}')
    print(f'Soma acumulada: {soma}')
```

Qual o valor da soma dos produtos de todos os Mercados?

```python
for mercado in lista_mercado:
  soma = 0
  for valor in mercado.values():
    soma = soma + valor
  print(f'Soma acumulada: {soma}')
#Soma acumulada: 74.64999999999999
#Soma acumulada: 59.019999999999996
#Soma acumulada: 56.599999999999994

```

qual valor médio do sabão em pó?

```python
soma = 0.0
for mercado in lista_mercado:
  print(mercado['Sabão em Pó'])
  soma = soma + mercado['Sabão em Pó']
media = soma/len(lista_mercado)
print(media)
```

## 🟣 **ESTRUTURAS CONDICIONAIS**:

*IF, ELSE e ELIF*

***sintaxe***

```python
if = se
elif = senão se
else = outro
if **condição:**
    print(executar condição)
elif **condição:**
    print(executar condição)
else:
    print(executar condição)

#se o primeiro bloco for verdadeiro --> executado
#senão se, o primeiro bloco for falso, e o segunda verdadeiro, o segundo vai ser executado
#outro: caso as duas primeiras condições sejam falsas, o terceiro bloco sera executado
```

```python
codigo_de_seguranca = '291'
codigo_de_seguranca_cadastro = '010'

if codigo_de_seguranca == codigo_de_seguranca_cadastro:
 print("Pagamento efetuado")
else:
 print("Erro: Código de segurança inválido")
```

```python
codigo_de_seguranca = '852'
codigo_de_seguranca_cadastro = '852'
senha = '7783'
senha_cadastro = '7783'

if (codigo_de_seguranca == codigo_de_seguranca_cadastro) & \
 (senha == senha_cadastro):
 print("Pagamento efetuado")
else:
 print("Erro: Pagamento não efetuado")
```

***exercicios***

***verificando se o numero é par ou impar***

```python
numero = 2
if numero % 2 == 0:
  print('o numero inserido é par')
else:
  print('o numero inserido é impar')
```

***verificando qual numero é maior***

```python
numero_1 = 4
numero_2 = 5
if numero_1 > numero_2:
  print(f'o numero {numero_1} é maior que o numero {numero_2}')
elif numero_2 > numero_1:
  print(f'o numero {numero_2} é maior que o numero {numero_1}')
else:
  ('os dois numero sao iguasi')
```

***verificando a entrada em um estabelecimento***

```python
idade = 18
if idade >= 18:
  print('voce pode entrar')
else:
  ('voce não pode entrar')
```

***calculo de desconto com base no valor da compra***

```python
valor_compra = 200
if valor_compra >= 100:
  desconto = valor_compra * 0.1
  valor_compra -= desconto
  print(f'voce ganhou desconto de 10% na sua compra, valor a pagar: {valor_compra}')
else:
    print('voce nao ganhou desconto')
```

***verificação de um número positivo, negativo ou zero***

```python
num = float(input("Digite um número: "))
if num > 0:
    print("O número é positivo.")
elif num < 0:
    print("O número é negativo.")
else:
    print("O número é zero.")
```

***verificação de vogal ou consoante***

```python
letra = 'a'
vogal = 'aeiou'
if letra in vogal:
  print('é uma vogal')
else:
    print('é uma consoante')
```

***identificação do maior entre 3 números***

```python
n1 = 2
n2 = 3
n3 = 5

maior = 0

if n1 > maior:
  maior = n1     #maior = 2
if n2 > maior:
  maior = n2     #maior = 3
if n3 > maior:
  maior = n3     #maior = 5
print(f'o maior numero é {maior}')

#vai atribuindo sempre o valor
```

***verificação de idade e categoria***

Crie um programa para determinar a categoria de um nadador de acordo com a idade fornecida pelo usuário. Por exemplo, se a idade estiver entre 5 e 7 anos, o programa deve imprimir "Infantil A"; entre 8 e 10 anos, imprimir "Infantil B"; e assim por diante.

```python
# 1, 2, 3, 4 ---> não posso participar
# 5, 6, 7 anos --> categoria A
# 8 ,9, 10 anos --> categoria B
#mais que 10 ---> categoria c
idade = 5


if idade >= 5 and idade <= 7:
    print("Categoria: Infantil A")

elif idade >= 8 and idade <= 10:
    print("Categoria: Infantil B")
elif idade > 10:
    print("Categoria: Categoria C")
else:
    print("Você não pode participar.")

#quando eu quero um valor ENTRE usar o operador lógico AND
#No primeiro if, a condição idade >= 5 and idade <= 7 verifica se a idade está entre 5 e 7 anos. Ambas as partes da condição precisam ser verdadeiras para que o bloco de código dentro desse if seja executado.
```

***Crie um programa que classifique uma pessoa em diferentes grupos de acordo com a idade.***

Por exemplo, se a idade estiver entre 0 e 12 anos, o programa deve imprimir "Criança"; entre 13 e 18 anos, imprimir "Adolescente"; entre 19 e 59 anos, imprimir "Adulto"; e acima de 60 anos, imprimir "Idoso".

```python
# 0 até 12 -> criança
# 13 até 18 -> adolescente
#19 até 59 -> adulto
#acima de 60 -> idoso

age = 65
if age <= 12:
  print('criança')
elif age >= 13 and age <= 18:
    print('adolescente')
elif age >= 19 and age <= 59:
    print('adulto')
else:
    print('idoso')
```

***verificação de numero primo***

Desenvolva um programa que verifique se um número fornecido pelo usuário é primo ou não. Um número primo é aquele que só é divisível por 1 e por ele mesmo.

```python
numero = 4
primo = numero / numero == 1 and numero / 1 == numero
# 2/2 = 1 , 2/1 = 2
if primo:
  print('é numero primo')
else:
  ('não é numero primo')
```

***sistema de autenticação***

Implemente um sistema de autenticação que armazene múltiplos usuários e senhas em um dicionário. O programa deve solicitar ao usuário um nome de usuário e senha e verificar se correspondem aos dados armazenados.

```python
# Dicionário para armazenar usuários e senhas
usuarios = {
    'usuario1': 'senha123',
    'usuario2': 'abcde',
    'usuario3': 'qwerty'
}

# Solicita ao usuário que insira nome de usuário e senha
usuario_input = input("Digite o nome de usuário: ")
senha_input = input("Digite a senha: ")

# Verifica se o usuário e senha correspondem aos dados armazenados no dicionário
if usuario_input in usuarios and usuarios[usuario_input] == senha_input:
#if usuario_input in usuarios = vendo se os valores que estao no usuario_input estão tambem no dicionario usuarios
#usuarios[usuario_input] == senha_input: o dicionario usuarios esta acessando os valores do usuario input, exemplo se eu digitar usuario1, o dicionario vai acessar esse valor que se chama chave
#o valor que esta armazenado nesta chave é senha123, e depois eu verifico se a senha digitada é igual o valor armazenado na chave: senha123
    print("Autenticação bem-sucedida! Bem-vindo,", usuario_input)
else:
    print("Usuário ou senha incorretos. Autenticação falhou.")
```

```python
propaganda_online = [
  {'tempo_gasto_site': 68.95, 'idade': 35, 'renda_area': 61833.90, 'tempo_gasto_internet': 256.09, 'cidade': 'Wrightburgh'},
  {'tempo_gasto_site': 80.23, 'idade': 31, 'renda_area': 68441.85, 'tempo_gasto_internet': 193.77, 'cidade': 'West Jodi'},
  {'tempo_gasto_site': 69.47, 'idade': 26, 'renda_area': 59785.94, 'tempo_gasto_internet': 236.50, 'cidade': 'Davidton'},
  {'tempo_gasto_site': 68.37, 'idade': 35, 'renda_area': 73889.99, 'tempo_gasto_internet': 225.58, 'cidade': 'South Manuel'},
  {'tempo_gasto_site': 88.91, 'idade': 33, 'renda_area': 53852.85, 'tempo_gasto_internet': 208.36, 'cidade': 'Brandonstad'},
  {'tempo_gasto_site': None, 'idade': 48, 'renda_area': 24593.33, 'tempo_gasto_internet': 131.76, 'cidade': 'Port Jefferybury'},
  {'tempo_gasto_site': 74.53, 'idade': 30, 'renda_area': 68862.00, 'tempo_gasto_internet': 221.51, 'cidade': 'West Colin'},
  {'tempo_gasto_site': 69.88, 'idade': 20, 'renda_area': 55642.32, 'tempo_gasto_internet': 183.82, 'cidade': 'Ramirezton'}
]
```

```python
for dado_de_usuario in propaganda_online:
    if dado_de_usuario['tempo_gasto_internet'] > 200:
        print(f"Cidade: {dado_de_usuario['cidade']}, Tempo Gasto no Site: {dado_de_usuario['tempo_gasto_site']}")
```

*try e except*
para lidar com erros

```python
numero = int(input('digite um numero'))
print(numero)
#se eu colcoar um valor que não seja numerico, o meu código vai parar pq vai dar erro, valueError
```

```python
try:
  numero_2 = int(input('digite um numero '))
  print(numero_2)
except ValueError:
  print('digite um numero valido')
finally:
  print('sempre executa')
```

```python
propaganda_online = [
  {'tempo_gasto_site': 68.95, 'idade': 35, 'renda_area': 61833.90, 'tempo_gasto_internet': 256.09, 'cidade': 'Wrightburgh'},
  {'tempo_gasto_site': 80.23, 'idade': 31, 'renda_area': 68441.85, 'tempo_gasto_internet': 193.77, 'cidade': 'West Jodi'},
  {'tempo_gasto_site': 69.47, 'idade': 26, 'renda_area': 59785.94, 'tempo_gasto_internet': 236.50, 'cidade': 'Davidton'},
  {'tempo_gasto_site': 68.37, 'idade': 35, 'renda_area': 73889.99, 'tempo_gasto_internet': 225.58, 'cidade': 'South Manuel'},
  {'tempo_gasto_site': 88.91, 'idade': 33, 'renda_area': 53852.85, 'tempo_gasto_internet': 208.36, 'cidade': 'Brandonstad'},
  {'tempo_gasto_site': None, 'idade': 48, 'renda_area': 24593.33, 'tempo_gasto_internet': 131.76, 'cidade': 'Port Jefferybury'},
  {'tempo_gasto_site': 74.53, 'idade': 30, 'renda_area': 68862.00, 'tempo_gasto_internet': 221.51, 'cidade': 'West Colin'},
  {'tempo_gasto_site': 69.88, 'idade': 20, 'renda_area': 55642.32, 'tempo_gasto_internet': 183.82, 'cidade': 'Ramirezton'}
]
```

3.1. Utilize a estrutura try/except para imprimir as cidades dos usuários que passaram mais de 70 segundos no site.

```python
for usuario in propaganda_online:
    try:
        if usuario['tempo_gasto_site'] > 70:
            print(usuario['cidade'])
    except TypeError:
        print('ignorar valor nulos')

#um dos valores que esta dentro da chave tempo_gasto_site é um NONE, o que significa que esse código daria erro, por isso, usar except de typeError para o código continuar
```

## 🟣 **ESTRUTURAS DE REPETIÇÃO**:

*FOR IN*
ele é uma estrutura de repetição utilizado em algum conjunto de valores: lista, dicionario…

```python
lista_produtos = ['iphone', 'ipad', 'samsung']
for produto in lista_produtos:
  print(produto)
#para cada produto na lista produtos, printa o produto
```

```python
lista_precos = [100, 200, 300, 400]
for preco in lista_precos:
  imposto = preco * 0.1
  print(imposto)
```

percorrendo um dicionario

```python
produtos_e_precos = {
    'iphone': 10,
    'tablet': 20,
    'notbook':30
}
for item in produtos_e_precos:
  print(item)
  print(produtos_e_precos[item])


  #p/ acessar o valor de um dicionario, acessamos pela chave
  #na primeira iteração do primeiro print(item), foi acessado a primeira chave 'iphone', sendo assim item agora é o iphone, assim sucessivamente, posteriormente no segundo print
  #foi acessado o dicionario de produtos_e_precos, e foi acessado o valor de cada item
```

***RANGE***

```python
list(range(5))
#vai começar em 0, pular de 1 em 1, até 4
#0 , 1, 2 ,3 4
```

```python
list(range(1, 5))
#vai começar em 1, pular de 1 em 1, até 4
#1, 2, 3, 4
```

```python
list(range(1,5,2))
#vai começar em 1, pular de 2 em 2, e vai ate 4
#1, 3
```

***RANGE NO FOR***

```python
for i in list(range(5)):
  print(i)
#o uso do list não é obrigatorio
```

```python
for i in (range(5)):
  print('oi')
```

```python
soma = 0
for numero in range(10):
  soma = soma + numero
  print(soma)

#0 - 1 - 2 - 3 - 4 - 5 -6 - 7 - 8 - 9
#a minha soma inicial começa c/ 0
#soma = soma + numero
#0 = 0 + 0 ---> imprimir 0
#0 = 0 + 1 ---> imprimi 1
#1 = 1 + 2 ---> imprimi 3
#3 = 3 + 3 ---> imorimi 6
#6 = 6 + 4 ---> impirmi 10
```

***ENUMERATE***

O **`enumerate`** em Python é uma função incorporada que permite iterar sobre uma sequência (como uma lista, tupla ou string) ao mesmo tempo em que obtém tanto o índice quanto o valor de cada elemento.

```python
           #fruta   #fruta   #fruta   #fruta
    ## 🟣 **ESTRUTURAS DE REPETIÇÃO**:      #indice0 #indice1 #indice2 #indice3
frutas = ['maçã', 'banana', 'uva', 'laranja']

for indice, fruta in enumerate(frutas):
    print(f'Índice: {indice}, Fruta: {fruta}')

Índice: 0, Fruta: maçã
Índice: 1, Fruta: banana
Índice: 2, Fruta: uva
Índice: 3, Fruta: laranja
```

```python
               vendedor   vendedor     vendedor
                  i          i            i
vendedores = ['amanda', 'guilherme', 'jussara']
qtd_vendas = [10, 20, 30]

for i, vendedor in enumerate(vendedores):
  print(vendedor)
  print(qtd_vendas[i])
```

*WHILE*

```python
contador = 0
while contador < 5:
    print(contador)
    contador += 1
```

→ atribuindo um valor de  0 para o contador

→ enquanto o contador for menor que 5

→ printa o contador

para que serve o incremento?

Se não incrementássemos o contador dentro do loop, a condição **`contador < 5`** nunca se tornaria falsa, e o loop continuaria executando infinitamente.

```python
contador = 0
while contador < 5:
    print(contador)
    # Não há incremento do contador aqui
```
Neste caso, o programa imprimiria o valor de contador (que inicialmente é 0) na primeira iteração, mas como não há incremento, contador sempre permaneceria igual a 0. Isso significa que a condição contador < 5 seria sempre verdadeira, porque 0 é sempre menor que 5.

Então, o loop continuaria repetindo o bloco de código dentro dele indefinidamente, sem nunca sair, pois a condição nunca seria falsa.

```python
contador = 1
while contador <= 5:
  input(f'nome: {contador} ' )
  contador += 1
#neste caso sera perguntado o nome da pessoa por 5 vezes
```

***WHILE TRUE***

```python
while True:
    resposta = input("Você deseja sair? (sim/não): ")
    if resposta.lower() == "sim":
        break
   
```

***BREAK***
serve para parar o código

```python
contador = 1
while contador <= 5:
  input(f'nome: {contador} ' )
  contador += 1
  break
#neste caso o loop vai iterar apenas uma vez e parar
```

```python
contador = 1
while contador <= 5:
  nome = input(f'nome: {contador} ' )
  contador += 1
  if nome == 'silvio':
    break
#neste caso o loop sera iterado por 5 vezes, porem ira parar qnd eu colocar o nome silvio
```

***continue***
pula para próxima linha

```python
contador = 1
while contador <= 5:
    nome = input(f'nome {contador}: ')
    if nome == 'silvio':
        continue
    contador += 1
#continue pula a proxima linha, no caso se colocar o nome silvio, nâo ira fazer a proxima iteração
```

neste caso, ele irá prosseguir o percurso normal, entretanto se eu colocar o nome silvio no nome 3, o nome 3 irá aparecer novamente, até eu colocar outro nome

## 🟣 **FUNÇÕES**:
uma função é criada para reutilizar um bloco de código

```python
print('----------------------------------')
print('sistema de alunos')
print('----------------------------------')
print('cadastro de funcionarios')
print('----------------------------------')
print('erro do sistema')
print('----------------------------------')
```
eu quero criar uma função para os (- - - - )

```python
def mostrarlinha():
  print('-' * 30)

mostrarlinha() #a função mostrar linha é chamada, e é executado o print
print('oi')
mostrarlinha()
print('ola')
mostrarlinha()
print('hello')
mostrarlinha()
```
vai me retornar →
-----------------------------
oi
----------------------------
ola
-----------------------------
hello
-----------------------------

***PARAMETROS***
agora eu quero fazer uma função p/ minha linha do meio 

```python

def mensagem(msg):
  print(msg)


mensagem('curso em video') #chamando a função mensagem, aonde o meu parametro msg, agora é curso em video
mostrarlinha()
mensagem('aprenda python')
mostrarlinha()
mensagem('erro do sistema')
mostrarlinha()
```

```python
a = 4
b = 5
s = a + b
print(s)

a = 2
b = 3
s = a + b
print(s)

a = 5
b = 9
s = a + b
print(s)

#9, 5, 14
```

***fazer uma função de soma***

```python
def soma(a, b):
  s = a + b
  print(s)


#programa principal
soma(4, 5) 
soma(2, 3)
soma(5, 9)
```

```python
def divisão(x, y):
  s = x / y
  print(s)

divisão(x = 10, y= 2) #vai me retornar 5
divisão(y = 10, x = 2) #vai me retornar 0.2
```

```python
#desempacotar parametros, colocar varios argumentos, independente de quantos parametros foi colocado
def contador(*num): # *é usado para desempacotar
    tam = len(num)
    print(f"recebi os numeros {num}, e são ao total {tam}")


contador(2, 3, 4) #me devolve uma tupla
contador(8, 0)
contador(2, 3, 4, 7, 6, 9, 1, 0)

#recebi os numeros (2, 3, 4), e são ao total 3
#recebi os numeros (8, 0), e são ao total 2
#recebi os numeros (2, 3, 4, 7, 6, 9, 1, 0), e são ao total 8
```

```python
def contador(*n):
  for valor in n:
    print(valor)

contador(2, 4)
#4
#2
```

```python
def contador (*num):
  for valor in num:
    multiplicar = valor * 2
    print(f'para os valores {valor}, eu obtenho o valor da multiplicação {multiplicar}')


contador(5, 2)
para os valores 5, eu obtenho o valor da multiplicação 10
para os valores 2, eu obtenho o valor da multiplicação 4
```

```python
def dobrar(lista):
  for valor in lista:
    print(valor * 2)

valores = [6, 3, 4]
dobrar(valores)

#12
#6
#8
```

```python
#somando uma lista
def soma_lista(lista):
  soma = 0
  for i in lista:
    soma = soma + i
  print(soma)

lista = list(range(1,10))
soma_lista(lista)

nova_lista = list(range(1,26))
soma_lista(nova_lista)

#eu não precisei fazer um for novamente
```

```python
def dividir(a, b: int) -> float: #o int depois do a e b, significa que o valor que vai ser colocado tem que ser um inteiro, e o int depois da seta, significa que o valor retornado sera um float
      print(a/b)

dividir(5, 3)
```

***exemplos de parâmetros***

parâmetros posicionais:

```python
def exemplo_parametros(posicao1, posicao2):
    # Código da função
exemplo_parametros(valor_1, valor_2)
#exemplo de chamada
```

parâmetros com valor padrão:
```python
def exemplo_parametros_valor_padrao(parametro1, parametro2=10):
    s = parametro1 + parametro2
    print(s)

exemplo_parametros_valor_padrao(20)

#o parametro 2 sempre terá o valor de 20, e no argumento eu passo apenas um parametro
#saida será 30
```

```python
#exemplo de como seria usado
def conectar_banco_dados(servidor, porta=5432, usuario='admin', senha='senha'):
    # Código para conectar ao banco de dados
```

parâmetros de lista:

```python
def exemplo_parametros_lista(lista_parametros):
    # Código da função
```

parâmetros de dicionários:

```python
def exemplo_parametros_dicionario(dicionario_parametros):
    # Código da fu
```

crie um programa aonde mostre se o aluno foi aprovado ou reprovado, usando função

```python
#return
def media(a,b):
  return(a+b)/2

#neste caso, foi criado uma função para fazer o calculo da média, entretanto n queremos exibir a nota e sim o resultado de aprovado ou não
#por isso é usado o return, pq vai retornar o a função, e no caso do print, não funcionaria pois ele não retorna a função, apenas exibe
```

```python
resultado = media(6,7)
if resultado >= 6:
  print('aprovado')
else:
  print('reprovado')
```

```python
lista_produtos = []
def cadastrar_produto():
  produto = input('digite o nome do produto ')
  produto = produto.casefold().capitalize()
  lista_produtos.append(produto)
  print(f'produto {produto} cadastrado com sucesso')
  print(f'lista de produtos atualizada {lista_produtos}')

for i in range(3):
  cadastrar_produto()


# criando uma lista de produtos vazia
#criando uma função que se chama cadastrar produto
#depois eu quero que essa minha função faça o seguinte: faça um input, perguntado o nome do produto, depois eu quero que este produto seja convertido em letras minusculas, sendo a primeira maiuscula
#depois quero jogar este produto na minha lista de produtos
#depois quero exibir o produto cadastrado e a lista atualizada
#quero que esse input apareça por 3 vezes
```

```python
#CRIANDO UM PROGRAMA QUE APAREÇA O INPUT INFINITAMENTE
# Lista de produtos inicialmente vazia
lista_de_produtos = []

def cadastrar_produto(lista_produtos): #criamos uma função cadastrar produto, aonde meu parametro é minha lista vazia
    while True:                        #criamos um while, enquanto for verdade, o input continuara aparecendo
        # Faz um input para obter o nome do produto
        produto = input("Digite o nome do produto (ou 'sair' para encerrar): ")

        # Verifica se o usuário quer sair
        if produto.lower() == 'sair':      #se o usuario digitar a palavra sair, o input será interrompido
            print("Encerrando o cadastro de produtos.")
            break

        # Converte o nome do produto para minúsculas com a primeira letra em maiúscula
        produto = produto.capitalize()

        # Adiciona o produto à lista de produtos
        lista_produtos.append(produto)

        # Exibe o produto cadastrado e a lista atualizada
        print(f"Produto cadastrado: {produto}")
        print(f"Lista de produtos atualizada: {lista_produtos}")
        

# Chama a função para cadastrar produtos
cadastrar_produto(lista_de_produtos)
```

## 🟣 **FUNÇÕES LAMBDA, MAP, FILTER E REDUCE**:

*FUNÇÃO LAMBDA*

* função temporarária no python

* usada para funções simples

```python
#FUNÇÕES X FUNÇÕES LAMBDA


#função
def calcular_imposto(preço, aliquota):
  return preço * aliquota


imposto = calcular_imposto(100, 0.3)
print(imposto)



#função lambda
                            #parametros      #o que vai me retornar
calcular_imposto2 = lambda valor, aliquota: valor * aliquota
imposto = calcular_imposto2(100, 0.3)
print(imposto)
```

função lambda com estruturas condicionais

```python
numero_e_par = lambda numero:'numero é par' if numero % 2 == 0 else 'numero é impar'
numero_e_par(10)
#numero é par
```

*função map*
-funciona como se fosse um for, percorre por cada elemento do meu iterável

```python
#map(funcao, iteravel)
preços = [100, 200, 300]

imposto = list(map(lambda preço: preço * 0.3, preços))
print(imposto)
#nesta função eu estou pegando, cada preço da minha tabela preços e multiplicando o valor por 0.3

#---------------------------------------------------#-----------------------------------------#-------------------------------#

multiplicação = lambda x: x * 2

resultado = list(map(multiplicação, preços))
print(resultado)
#no caso eu coloquei a função lambda diretamente dentro da função maps pela variavel multiplicação, só funciona dessa forma se eu ja tiver um parametro definido, neste caso foi o 2


#30, 60, 90
#200, 400, 600
```

*função filter*

- usada para filtrar elementos de iteráveis, com base em uma função que deve retornar um booleano

```python
preços = [100, 200, 300]

def filtrar_aumento(preco):
  if preco < 200:
     return True
  else:
    return False


preço_menor_200 = list(filter(filtrar_aumento, preços))
print(preço_menor_200)
#me retorna 100, pois é o unico valor menor que 200
```

```python
# Definindo uma lista de números
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Usando filter com uma função lambda para filtrar números pares
numeros_pares = list(filter(lambda x: x % 2 == 0, numeros))

# Resultado
print(numeros_pares)
```

*função reduce*

A função reduce é útil em situações em que você precisa realizar uma operação cumulativa em todos os elementos de uma sequência

```python
from functools import reduce

# Definindo uma lista de números
numeros = [1, 2, 3, 4, 5]

# Usando reduce para calcular a soma dos números
soma = reduce(lambda x, y: x + y, numeros)  #ele sempre soma de 2 em 2

# Resultado
print(soma)
```

*FUNÇÕES DE ALTA ORDEM*

- funções que retornam funções

```python
# Exemplo usando uma função que retorna outra função
def multiplicador(n):      #função mutiplicador que recebe como parametro n
    return lambda x: x * n   #vai me retornar uma função lambda que recebe x * n

duplicador = multiplicador(2)  #criei uma variavel chamada duplicador que vai receber a minha função multiplicador e agora meu n, corresponde a 2, e essa 
                               #função multiplicador retorna minha função lambda, que aceita um valor x 

print(duplicador(5))  # Saída: 10   #aqui eu passei meu valor de x, que no caso é 5
```

## 🟣 **PROGRAMAÇÃO ORIENTADA A OBJETO**:

*classes*

classes -> são um bloco de código que, você pode encapsular dados (objetos, atributos e métodos)

ex: criar uma classe chamada alunos, dentro dessa classe eu terei o nome do aluno, a idade e as notas e dentro dessa classe eu vou calcular a média dos alunos

quando eu for chamar essa classe, eu vou atribuir meus alunos há ela, ex: aluno1, aluno2

objetos = aluno1, aluno2

 atributos = caracteristicas desses alunos: nome, idade e notas

 método = calcular a média (o que eu vou fazer come esses dados)

**CLASSES X DICIONÁRIOS**

dicionários = apenas armazenam informações, então eles não são capazes de fazer algo com esses dados

```python
#classes

class Aluno:  #criei uma classe chamada aluno
    def __init__(self, nome, idade, notas):   #defini os atributos que minha classe vai ter
        self.nome = nome
        self.idade = idade
        self.notas = notas

    def calcular_media(self):              #criei uma função chamada calcular media
        média = sum(self.notas) / len(self.notas)  #criei uma variavel, aonde vai armazenar o meu calculo da média

        if média < 6:                      #se a minha média for menor que 6, ta reprovado
            return média,'reprovado'       # vou retornar uma tupla, com a minha média e o aprovado
        else:
            return média,'aprovado'

# Criando instâncias da classe Aluno
aluno1 = Aluno(nome="João", idade=17, notas=[9, 10, 6])      #criei uma variavel chamada aluno1 que armazena minha classe aluno, aonde eu vou atribuir valoes aoas meus atributos
aluno2 = Aluno(nome="Maria", idade=16, notas=[7, 5, 8])

# Acessando atributos e métodos
#print(f"{aluno1.nome} foi {média}")   eu não consigo acessar dessa forma, pois média é apenas uma variavel criada dentro do meu escopo da função calcular_media, então para retornar o valor eu precisoa acessar diretamente a minha função
print(f"{aluno1.nome} foi {aluno1.calcular_media()}")
print(f"{aluno2.nome} foi {aluno2.calcular_media()}")

#João foi (8.333333333333334, 'aprovado')
#Maria foi (6.666666666666667, 'aprovado')
```

```python
class Aluno:
    def __init__(self, nome, idade, notas):
        self.nome = nome
        self.idade = idade
        self.notas = notas
        self.media, self.status = self.calcular_media()  #média = média, status = aprovado ou reprovado

    def calcular_media(self):
        média = sum(self.notas) / len(self.notas)

        if média < 6:
            return média, 'reprovado'
        else:
            return média, 'aprovado'

# Criando instâncias da classe Aluno
aluno1 = Aluno(nome='joão',idade=17, notas=[9, 10, 6])
aluno2 = Aluno(nome="Maria", idade=16, notas=[7, 5, 8])

# Acessando atributos e métodos
print(f"{aluno1.nome} foi {aluno1.status} com média {aluno1.media}")
print(f"{aluno2.nome} foi {aluno2.status} com média {aluno2.media}")

#joão foi aprovado com média 8.333333333333334
#Maria foi aprovado com média 6.66666666666666
```

```python
class ControleRemoto:
  def __init__(self, nome_cor, valor_altura,):
      self.cor = nome_cor
      self.valor = valor_altura
  def aumentar_diminuir_volume(self, botão):
    if botão == '+':
      return('aumentou volume')
    elif botão == '-':
      return('diminuiu volume')
    else:
      return('não fez nada')


ControleRemoto1 = ControleRemoto(nome_cor = 'preto', valor_altura = 5)
ControleRemoto2 = ControleRemoto(nome_cor = 'cinza', valor_altura = 8)

#acessando uma caracteristica do controle remoto
print(ControleRemoto1.cor)
#preto

#acessando a função do controle remoto
ControleRemoto1.aumentar_diminuir_volume('+')
#aumentar volume



ação = ControleRemoto2.aumentar_diminuir_volume('-')
print(f'o controle {ControleRemoto1.cor} {ação} ')

#preto
#o controle preto diminuiu volume
```





























