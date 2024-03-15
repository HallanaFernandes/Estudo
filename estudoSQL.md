
# 🔹 SQL

## 🟣 **COMANDO SELECT E ORDER BY**:
   
**selecionando tudo de uma tabela** 

   ```sql
   select * from tabela
   ```
**selecionando colunas especificas**

   ```sql
   select nome_coluna, nome_coluna from tabela
   ```
**selecionando colunas especificas e modificando o nome delas**

   ```sql
select nome_coluna as 'nome_que_quero_dar' from tabela
```
**selecionando limite de linhas**

   ```sql
  select * from tabela limit 2 --seria selecionado as duas primeiras linhas 
   ```
**ORDER BY**
classificar os resultados de acordo com uma ou mais colunas em uma ordem especifica

   ```sql
select * from tabela order by nome_coluna -- alterna de forma crescente
   ```

   ```sql
 select * from tabela order by nome_coluna desc --alterna de forma decrescente 
   ```
## 🟣 **CONCATENAÇÃO**:

   ```sql
 SELECT 
    CONCAT(coluna_1, ' ', coluna_2) AS nome
FROM tabela
   ```

## 🟣 **COMANDO WHERE (filtros)**:
operadores utilizados: 
operador de igual: =
operador de menor que: <
operador de maior que: >
operador de diferente de: !

filtrando por valor
   ```sql
   select * from tabela where coluna = `x`
   ```
filtrando por data
```sql
select * tabela where coluna = `2019-01-03 
```
## 🟣 **OPERADORES**:

**OPERADORES AND E OR**:
servem para aplicar dois filtros ao mesmo tempo 

```sql
select * tabela where coluna1 = 'x’ and coluna2 = 'y'
```
**OPERADOR NOT**:
ele é usado juntamente com outros comparadores lógicos

Por exemplo, se você quiser selecionar todos os clientes que não são da cidade de "New York"
  
```sql
SELECT * FROM clientes WHERE NOT cidade = 'New York'
```

```sql
SELECT * FROM clientes WHERE NOT (cidade = 'New York' AND idade > 30)
-- na tabela n pode ter a cidade nova york e também não pode ter idade maior q 30
-- tem que atender as duas condições p não entrar
```
 **OPERADOR LIKE**:
selecionar clientes que começam com a letra A:

```sql
SELECT * FROM clientes WHERE nome LIKE 'A%';
```
selecionar os clientes que terminam com a letra A:

```sql
SELECT * FROM clientes WHERE nome LIKE '%a';

```
selecionar todos os nomes que tenham a segunda letra A:

```sql
SELECT * FROM clientes WHERE nome LIKE '_A%';
```
para selecionar nomes que começam com A e terminam com E:

```sql
SELECT * FROM clientes WHERE nome LIKE 'A%E';
```
obs:  a porcentagem no final, é para quando queremos que a letra esteja no inicio

a porcentagem no inicio, é para quando queremos que a letra esteja no final

**OPERADOR BETWEEN**:
usado para trabalhar com intervalos
Por exemplo, se você tiver uma tabela de produtos com uma coluna de preço e quiser selecionar todos os produtos com preço entre $10 e $20

```sql
SELECT * FROM produtos
WHERE preco BETWEEN 10 AND 20;
```
**OPERADOR IN**:
para verificar se um valor está presente em um conjunto de valores especificado.

```sql
SELECT * FROM tabela
WHERE coluna IN (valor1, valor2, valor3, ...);
```

## 🟣 **FUNÇÕES DE AGREGAÇÃO**:

**COUNT**
contando a quantidade de valores de uma coluna

Obs: ele ignora os valores nulos

```sql
select count (nome da coluna) from tabela;
```

**COUNT(*)**
retorna a quantidade total de valores de uma coluna sem ignorar valores nulos, serve para contar quantas linhas tem a tabela

```sql
select count(*) from tabela
```
**COUNT(distinct)**
etorna uma contagem distinta de valores de uma coluna, ex: eu quero saber quantos niveis de escolaridade a minha coluna tem
```sql
select count (distinct coluna) from tabela;
```
outras funções de agregação:
SUM - soma
AVG - média
MIN - valor minimo 
MAX - valor máximo


## 🟣 **FUNÇÕES MATEMÁTICAS**:

**ABS**
é uma função que retorna o valor absoluto de um número. O valor absoluto de um número é sua distância em relação a zero na reta numérica.

Salário máximo para o departamento de engenharia 

```sql
(MAX(salary_eng)) = 4000
```
Salário máximo para o departamento de marketing 
```sql
(MAX(salary_marketing)) = 5000
```
calculando 
```sql
MAX(salary_eng) - MAX(salary_marketing), obterá um resultado de 4000 - 5000 = -1000.
```
 Nesse caso, a diferença será negativa. Ao aplicar a função ABS esse valor sempre será positivo

## 🟣 **GROUP BY**:
ele é usado para agrupar dados iguai
Tabela: first_name
_____________________
|   id   |   name   |
|--------|----------|
|   1    |   John   |
|   2    |   Emily  |
|   3    |  Michael |
|   4    |  Sophia  |
|   5    |   John   |
|   6    |   Emma   |
|   7    | William  |
|   8    |  Olivia  |
|   9    |  Michael |
|   10   |   Ava    |
¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯

```sql
select name from first_name 
group by name
```
-- isso vai me retornar apenas os nomes sem repetição

|   name   |
|----------|
|   John   |
|   Emily  |
|  Michael |
|  Sophia  |
|   Emma   |
| William  |
|  Olivia  |
|   Ava    |

é usado para agrupar linhas que tenham o mesmo valor em uma ou mais colunas, permitindo então a aplicação de funções de agregação, como SUM, COUNT, AVG, MAX, MIN

| Nome  | Classe | Nota |
|-------|--------|------|
| Alice |   A    |  90  |
| Bob   |   B    |  85  |
| Carol |   A    |  95  |
| Dave  |   B    |  80  |
| Eve   |   A    |  88  |

fazer uma média por classe

```sql
SELECT classe, AVG(nota) AS media_notas
FROM alunos
GROUP BY classe;
-- selecionando a classe, aonde vai ser agrupado por dados iguais, no caso, teria apenas a classe A e a classe B
-- vou fazer uma média das notas que vai se chamar média notas
-- da minha tabela alunos
-- agrupar por classe
```
resultado:
| Classe | Média_Notas |
| ------ | ----------- |
| A      | 91          |
| B      | 82.5        |

sintaxe:

```sql
SELECT coluna_que_quero_agrupar, funcao_agregacao(coluna) as nome_da_nova_coluna
FROM tabela
GROUP BY coluna_que_quero_agrupar;
```
**HAVING**
A cláusula HAVING é utilizada em consultas SQL para aplicar condições de filtro a grupos de linhas resultantes de uma operação GROUP BY. Ela é semelhante à cláusula WHERE, mas enquanto a WHERE é usada para filtrar linhas individuais antes do agrupamento, a HAVING é usada para filtrar grupos após o agrupamento ter sido feito.

Por exemplo, suponha que você tenha uma tabela de vendas com informações sobre vendas de produtos e gostaria de encontrar o total de vendas para cada produto, mas apenas para produtos cujo total de vendas seja maior que 100.000. Você poderia usar uma consulta com GROUP BY e HAVING da seguinte forma:

```sql

SELECT 
    product_id,
    SUM(sales_amount) AS total_sales
FROM 
    sales
GROUP BY 
    product_id
HAVING 
    SUM(sales_amount) > 100000;

```
Neste exemplo, a cláusula **`GROUP BY`** é usada para agrupar as vendas por **`product_id`**, e então a cláusula **`HAVING`** é usada para filtrar apenas os grupos cujo total de vendas (**`SUM(sales_amount)`**) é maior que 100.000.


## 🟣 **JOIN**:
Chave Primária:

É um atributo ou conjunto de atributos que identifica unicamente cada registro em uma tabela de banco de dados. Deve ser único para cada registro e não nulo.

Chave Estrangeira:

É um campo em uma tabela que faz referência à chave primária de outra tabela. É usada para estabelecer uma relação entre duas tabelas, garantindo a integridade referencial.

Tabela Fato:

É uma tabela em um modelo de banco de dados dimensional que armazena dados de negócios ou eventos que ocorrem em um processo específico. Geralmente contém medidas quantitativas ou fatos sobre o processo.

Tabela Fato:

É uma tabela em um modelo de banco de dados dimensional que armazena dados de negócios ou eventos que ocorrem em um processo específico. Geralmente contém medidas quantitativas ou fatos sobre o processo.

INNER JOIN

Retorna apenas as linhas onde há correspondência nas duas tabelas. Se não houver correspondência para uma linha em uma das tabelas, essa linha não será incluída no resultado.

LEFT JOIN
Retorna todas as linhas da tabela à esquerda da cláusula **`LEFT JOIN`** (tabela da esquerda), independentemente de haver correspondência na tabela à direita (tabela da direita). Se não houver correspondência para uma linha na tabela à direita. As colunas da tabela da direita terão valores NULL no resultado

RIGHT JOIN
Retorna todas as linhas da tabela à direita da cláusula **`RIGHT JOIN`** (tabela da direita), independentemente de haver correspondência na tabela à esquerda (tabela da esquerda). Se não houver correspondência para uma linha na tabela à esquerda, as colunas da tabela à esquerda terão valores NULL no resultado.

FULL JOIN
inclui todas as linhas das tabelas da esquerda e da direita, combinando as linhas onde há correspondência e preenchendo as colunas com valores NULL onde não há correspondência.

Tabela "alunos"

Colunas: id_aluno (chave primária), nome_aluno, idade
Tabela "notas"

| id_aluno | nome_aluno | idade |
|----------|------------|-------|
|    1     |   Alice    |  18   |
|    2     |    Bob     |  20   |
|    3     |   Carol    |  19   |


Tabela "Notas"
Colunas: id_nota (chave primária), id_aluno (chave estrangeira referenciando id_aluno na tabela "alunos"), nota

| id_nota | id_aluno | nota |
|---------|----------|------|
|    101  |    1     |  85  |
|    102  |    2     |  90  |
|    103  |    3     |  88  |


```sql
SELECT alunos.nome_aluno, notas.nota
FROM alunos
INNER JOIN notas ON alunos.id_aluno = notas.id_aluno;
```
resultado:
| nome_aluno | nota |
|------------|------|
|   Alice    |  85  |
|    Bob     |  90  |
|   Carol    |  88  |


## 🟣 **VARIÁVEIS**:
tipos de variáveis:

INT - números inteiros
VARCHAR - texto
DECIMAL ou NUMERIC - numeros decimais
DATA ou DATETIME - datas
BIT ou BOOLEAN - valores booleanos (o valor 1, corresponde ao booleano true e o valor 0 corresponde ao booleano false)
FLOAT ou REAL - para valores precisos

para declarar uma variável:

```sql
declare @nome_variável tipo_variável(qtd de caractere se for texto)
```
para atribuir um valor a variável
```sql
set @nome_variaável = 'valor'
```



```sql

```
```sql

```