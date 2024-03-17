
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

filtando por valor
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
***Chave Primária:***

É um atributo ou conjunto de atributos que identifica unicamente cada registro em uma tabela de banco de dados. Deve ser único para cada registro e não nulo.

***Chave Estrangeira:***

É um campo em uma tabela que faz referência à chave primária de outra tabela. É usada para estabelecer uma relação entre duas tabelas, garantindo a integridade referencial.

***Tabela Fato:***

É uma tabela em um modelo de banco de dados dimensional que armazena dados de negócios ou eventos que ocorrem em um processo específico. Geralmente contém medidas quantitativas ou fatos sobre o processo.

***Tabela Dimensão:***

É uma tabela em um modelo de banco de dados dimensional que contém atributos descritivos e contextuais que fornecem detalhes sobre os dados armazenados na tabela fato. Esses atributos ajudam a filtrar, agrupar e classificar os dados na tabela fato.

***INNER JOIN:***

Retorna apenas as linhas onde há correspondência nas duas tabelas. Se não houver correspondência para uma linha em uma das tabelas, essa linha não será incluída no resultado.

***LEFT JOIN:***

Retorna todas as linhas da tabela à esquerda da cláusula **`LEFT JOIN`** (tabela da esquerda), independentemente de haver correspondência na tabela à direita (tabela da direita). Se não houver correspondência para uma linha na tabela à direita. As colunas da tabela da direita terão valores NULL no resultado

***RIGHT JOIN:***

Retorna todas as linhas da tabela à direita da cláusula **`RIGHT JOIN`** (tabela da direita), independentemente de haver correspondência na tabela à esquerda (tabela da esquerda). Se não houver correspondência para uma linha na tabela à esquerda, as colunas da tabela à esquerda terão valores NULL no resultado.

***FULL JOIN:***

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

BIT ou BOOLEAN - valores booleanos (o valor 1, 
corresponde ao booleano true e o valor 0 corresponde ao booleano false)

FLOAT ou REAL - para valores precisos

para declarar uma variável:

```sql
declare @nome_variável tipo_variável(qtd de caractere se for texto)
```
para atribuir um valor a variável
```sql
set @nome_variaável = 'valor'
```
## 🟣 **SUBQUERIES**:
consulta dentro de outra consulta

| Funcionário | Salário |
|-------------|---------|
|    João     |   3000  |
|    Maria    |   3500  |
|    Pedro    |   4000  |
|     Ana     |   4200  |
|    Lucas    |   4500  |

calculando a média de salários

```sql
SELECT AVG(SALARIO) FROM TABELA;
-- 3840
```
selecionando os funcionarios que tem salario superior a média

```sql
SELECT * FROM TABELA WHERE SALARIO > 3840;
-- pedro, ana, lucas
```
só que dessa forma, caso seja colocado um novo funcionário na tabela, o filtro será feito de forma errada

Para ficar dinâmico, é necessário utilizar subqueries

```sql
SELECT * FROM TABELA WHERE SALARIO > (SELECT AVG(SALARIO) FROM TABELA);
```

## 🟣 **VIEWS**:

uma janela que oferece uma visão específica dos dados em um banco de dados. Ela não armazena dados por si só, mas é uma consulta armazenada que retorna um conjunto de resultados baseado nos dados das tabelas subjacentes. É como criar uma nova perspectiva sobre os dados existentes, permitindo que você veja apenas as informações relevantes para uma determinada consulta ou relatório, sem precisar modificar a estrutura subjacente do banco de dados.


| Funcionário      | Departamento | Salário    |
|------------------|--------------|----------- |
| João Silva       | Vendas       | R$ 3500.00 |
| Maria Santos     | Marketing    | R$ 4200.00 |
| Pedro Oliveira   | TI           | R$ 5000.00 |
| Ana Costa        | RH           | R$ 3800.00 |
| Carlos Mendes    | Financeiro   | R$ 4600.00 |


View que calcule o salário líquido dos funcionários, com base no salário bruto e em um desconto fixo de imposto de 10%.

```sql
CREATE VIEW salario_liquido AS
SELECT id, nome, salario_bruto * 0.9 AS salario_liquido
FROM funcionarios;
SELECT * FROM salario_liquido;
```

iria criar uma nova tabela com os valores dos salários líquidos

```sql
| Funcionário      | Departamento | Salário Líquido |
|------------------|--------------|-----------------|
| João Silva       | Vendas       | R$ 3150.00      |
| Maria Santos     | Marketing    | R$ 3780.00      |
| Pedro Oliveira   | TI           | R$ 4500.00      |
| Ana Costa        | RH           | R$ 3420.00      |
| Carlos Mendes    | Financeiro   | R$ 4140.00      |
```
Para alterar uma view - ALTER VIEW
para excluir uma viwe - DROP VIEW


## 🟣 **CRUD**:

CREATE:

criar um novo banco de dados

```sql
CREATE DATABASE exemplo;
```
criando uma nova tabela

```sql
CREATE TABLE nome (coluna1 tipo1, coluna2 tipo2);
```

INSERT:

```sql
INSERT INTO tabela(coluna1, coluna2, coluna3)
VALUES
(valor1, valor2, valor3),
(valor1, valor2, valor3).
```

UPDATE:
para modificar linhas

```sql
UPDATE tabela
set coluna = valor
where coluna = valor
```
DELETE:
excluir linhas

```sql
DELETE from alunos
where ID_aluno = 2
```
ALTER TABLE:
modificar colunas

```sql
-- adicionando uma coluna
ALTER TABLE tabela
ADD coluna tipo;
```

```sql
-- modificando o tipo 
ALTER TABLE tabela
MODIFY coluna novo_tipo;
```

```sql
-- renomeando uma coluna
ALTER TABLE tabela
CHANGE nome_antigo nome_novo tipo;

```

DROP:
excluir a tabela inteira

```sql
DROP TABLE exemplo;
```
DROP DATABASE:
excluir banco de dados

```sql
DROP DATABASE exemplo;
```
## 🟣 **FUNÇÕES CONDICIONAIS**:

sintaxe:

```sql
select 
		coluna1,
		coluna2,
	  case
			  when condição then resultado1
			  when condição then resultado2
			  else result
		end as -- para dar um nome a nova coluna
 from tabela;
```

exemplo:
| Nome Produto | Preço Unitário |
|--------------|----------------|
| Smartphone   |      $500      |
| Laptop       |     $1200      |
| Headphones   |      $100      |
| Smart TV     |      $800      |
| Tablet       |      $600      |

classificar os produtos de acordo com o preço_unit

→ os produtos que forem maior ou igual a 3.000 serão da classe A

→ os produtos que forem menor do que 3.000 serão da classe B


```sql
SELECT 
		nome_produto,
		preco_unit,
	  case
			  when preco_unit >= 3.000 then 'classe A'
			  else 'classe b'
		 end as classe_produto -- (para criar uma nova coluna aonde terá os nomes de classe A e classe B)
	from produtos;
	
```
## 🟣 **FUNÇÃO JANELA**:

OVER() →as operações são realizadas para cada linha da tabela. Isso inclui opções como particionar os dados em grupos distintos (usando PARTITION BY) ou ordenar as linhas dentro desses grupos (usando ORDER BY).

***USANDO APENAS O OVER***

calcula a média de todos os valores de vendas sem levar em consideração a ordem das linhas na tabela. Assim, o valor da média será o mesmo para todas as linhas.

| id  | valor |
|-----|-------|
|  1  |  100  |
|  2  |  150  |
|  3  |  200  |
|  4  |  120  |


```sql
SELECT id, valor, AVG(valor) OVER () AS media_valor
FROM vendas;
-- over vai criar uma nova coluna aonde vai ser chamada de média de valor
-- aplicar essa média para todas as linhas da minha coluna
```
resultado:

| id  | valor | media_valor |
|-----|-------|-------------|
|  1  |  100  |    142.5    |
|  2  |  150  |    142.5    |
|  3  |  200  |    142.5    |
|  4  |  120  |    142.5    |

***USANDO O OVER E O ORDER BY:***

```sql
SELECT id, valor, AVG(valor) OVER (ORDER BY id) AS media_valor
FROM vendas;
-- estou fazendo uma média por linha
```
| id  | valor | media_valor |
|-----|-------|-------------|
|  1  |  100  |    100      |
|  2  |  150  |    125      |
|  3  |  200  |    150      |
|  4  |  120  |    142.5    |

uando usamos a cláusula ORDER BY, a função de janela AVG() OVER (ORDER BY id) calcula a média dos valores de vendas considerando a ordem dos IDs das vendas. Isso significa que cada linha terá a média dos valores de vendas até aquele ponto, considerando a ordem crescente dos IDs.
* Na primeira linha, o valor de venda é 100. A média dos valores até esse ponto (considerando apenas a venda com ID 1) é 100

***USANDO O OVER E O PARTITION BY:***
| id_loja | nome_loja | regiao  | qtd_vendida |
|---------|-----------|---------|-------------|
|  123    |  Loja_47  |  Norte  |    345      |
|  456    |  Loja_82  |  Sul    |    567      |
|  789    |  Loja_19  |  Leste  |    213      |
|  234    |  Loja_64  |  Oeste  |    789      |
|  567    |  Loja_33  | Central |    432      |
|  890    |  Loja_91  |  Norte  |    654      |
|  321    |  Loja_76  |  Sul    |    123      |
|  654    |  Loja_12  |  Leste  |    876      |
|  987    |  Loja_57  |  Oeste  |    234      |
|  432    |  Loja_88  | Central |    543      |

```sql
SELECT 
    id_loja, 
    nome_loja, 
    regiao, 
    qtd_vendida, 
    SUM(qtd_vendida) OVER(PARTITION BY regiao) AS total_vendido_por_regiao 
FROM 
    lojas;

```
| id_loja | nome_loja | regiao  | qtd_vendida | total_vendido_por_regiao |
|---------|-----------|---------|-------------|--------------------------|
|  123    |  Loja_47  |  Norte  |    345      |           999            |
|  890    |  Loja_91  |  Norte  |    654      |           999            |
|  456    |  Loja_82  |  Sul    |    567      |           690            |
|  321    |  Loja_76  |  Sul    |    123      |           690            |
|  789    |  Loja_19  |  Leste  |    213      |           1089           |
|  654    |  Loja_12  |  Leste  |    876      |           1089           |
|  567    |  Loja_33  | Central |    432      |           975            |
|  432    |  Loja_88  | Central |    543      |           975            |
|  987    |  Loja_57  |  Oeste  |    234      |           1023           |
|  234    |  Loja_64  |  Oeste  |    789      |           1023           |


***RANK:***
| Nome do Aluno | Nota |
|---------------|------|
|   João        |  85  |
|   Maria       |  92  |
|   Pedro       |  78  |
|   Ana         |  92  |
|   Lucas       |  85  |


```sql
SELECT 
    nome_aluno,
    nota,
    RANK() OVER (ORDER BY nota DESC) AS classificacao
FROM 
    alunos;

```
resultado:
| Nome do Aluno | Nota | Classificação |
|---------------|------|---------------|
|   Maria       |  92  |       1       |
|   Ana         |  92  |       1       |
|   João        |  85  |       3       |
|   Lucas       |  85  |       3       |
|   Pedro       |  78  |               |

Os alunos Maria e Ana têm a nota mais alta (92), portanto, ambos recebem a classificação 1.

Os alunos João e Lucas têm a segunda maior nota (85), então ambos recebem a classificação 3, e a próxima classificação seria 4, mas como há dois alunos empatados em 3, o próximo número é 5.

O aluno Pedro tem a nota mais baixa (78) e, portanto, recebe a classificação 5.

Assim, a função RANK nos permite classificar os alunos de acordo com suas notas, criando uma ordem de classificação baseada em critérios específicos, neste caso, a nota.

***RANK X DENSE_RANK***

****RANK()****

A função RANK() atribui classificações às linhas em que ocorrem empates, pulando números conforme necessário. Isso significa que, se houver empates, as classificações subsequentes são puladas.

Por exemplo, se dois registros tiverem a mesma classificação, a próxima classificação não será 2, mas sim 3.

A diferença entre as classificações é igual ao número de classificações que precedem uma linha, mais 1.

****DENSE_RANK():****

A função DENSE_RANK() atribui classificações às linhas em que ocorrem empates, mas não pula números. Em vez disso, a classificação subsequente é incrementada por 1, independentemente de haver empates.

Isso significa que não há lacunas nas classificações quando ocorrem empates. Cada linha recebe uma classificação única, e a diferença entre as classificações é sempre 1.

Portanto, mesmo que haja empates, a próxima classificação ainda será incrementada em 1.

***MÉDIA E SOMA MÓVEL***

| DataFechamento | FaturamentoMM |
|----------------|---------------|
| 2020-01-01     | 8             |
| 2020-02-01     | 10            |
| 2020-03-01     | 6             |
| 2020-04-01     | 9             |
| 2020-05-01     | 5             |
| 2020-06-01     | 4             |
| 2020-07-01     | 7             |
| 2020-08-01     | 11            |
| 2020-09-01     | 9             |
| 2020-10-01     | 12            |
| 2020-11-01     | 11            |
| 2020-12-01     | 10            |

```sql
SELECT *, AVG(FaturamentoMM) OVER (ORDER BY DataFechamento ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING) AS "fat. acum" 
FROM Resultado;
```
ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING: DEFINE O INTERVALO QUE VAI SER USADO. Define a janela deslizante que será usada para calcular a média móvel. Aqui, estamos incluindo a linha atual (CURRENT ROW) e as linhas anterior (1 PRECEDING) e seguinte (1 FOLLOWING) à linha atual na janela. Isso significa que a média será calculada considerando os valores da linha atual, da linha anterior e da linha seguinte à linha atual.

***FUNÇÃO LAG***

```sql
LAG(column_name, offset, default_value) OVER (ORDER BY order_column)
```
é usada para acessar o valor de uma coluna em uma linha anterior em relação à linha atual em um conjunto de resultados. Ela é comumente usada para calcular diferenças ou variações entre valores consecutivos em uma tabela.

- **`column_name`**:

 O nome da coluna da qual você deseja acessar o valor anterior.
- **`offset`**: 

O número de linhas antes da linha atual da qual você deseja acessar o valor. Se omitido, o padrão é 1, o que significa que a função retorna o valor da linha anterior.
- **`default_value`**:

 Um valor padrão a ser retornado se a linha anterior não estiver disponível (por exemplo, se for a primeira linha do conjunto de resultados).
- **`ORDER BY order_column`**:

 Especifica a ordem em que as linhas devem ser consideradas para determinar a "linha anterior".

| Data       | Vendas |
|------------|--------|
| 2022-01-01 | 100    |
| 2022-01-02 | 120    |
| 2022-01-03 | 150    |
| 2022-01-04 | 130    |
| 2022-01-05 | 140    |


```sql
SELECT
    Data,
    Vendas,
    LAG(Vendas, 1, 0) OVER (ORDER BY Data) AS Vendas_Anteriores                
FROM
    Vendas;
```
resultado:

| Data       | Vendas | Vendas_Anteriores |
|------------|--------|-------------------|
| 2022-01-01 | 100    | 0                 |
| 2022-01-02 | 120    | 100               |
| 2022-01-03 | 150    | 120               |
| 2022-01-04 | 130    | 150               |
| 2022-01-05 | 140    | 130               |

tabela: resultado
| DataFechamento | FaturamentoMM |
|----------------|---------------|
| 2020-01-01     | 8             |
| 2020-02-01     | 10            |
| 2020-03-01     | 6             |
| 2020-04-01     | 9             |
| 2020-05-01     | 5             |
| 2020-06-01     | 4             |
| 2020-07-01     | 7             |
| 2020-08-01     | 11            |
| 2020-09-01     | 9             |
| 2020-10-01     | 12            |
| 2020-11-01     | 11            |
| 2020-12-01     | 10            |
| 2019-12-01     | 20            |
| 2019-11-01     | 30            |
| 2019-10-01     | 24            |


```sql
SELECT
    *,
    LAG(FaturamentoMM, 1, FaturamentoMM) OVER (ORDER BY DataFechamento) AS desloc
FROM
    resultado;
```

| DataFechamento | FaturamentoMM | desloc |
|----------------|---------------|--------|
| 2019-10-01     | 24            | 24     |
| 2019-11-01     | 30            | 24     |
| 2019-12-01     | 20            | 30     |
| 2020-01-01     | 8             | 20     |
| 2020-02-01     | 10            | 8      |
| 2020-03-01     | 6             | 10     |
| 2020-04-01     | 9             | 6      |
| 2020-05-01     | 5             | 9      |
| 2020-06-01     | 4             | 5      |
| 2020-07-01     | 7             | 4      |
| 2020-08-01     | 11            | 7      |
| 2020-09-01     | 9             | 11     |
| 2020-10-01     | 12            | 9      |
| 2020-11-01     | 11            | 12     |
| 2020-12-01     | 10            | 11     |

***ánalise month-over-month (MOM)***

```sql
SELECT 
    *, 
    LAG(FaturamentoMM, 1, FaturamentoMM) OVER (ORDER BY DataFechamento) AS desloc,
    (FaturamentoMM / LAG(FaturamentoMM, 1, FaturamentoMM) OVER (ORDER BY DataFechamento) - 1) * 100 AS '%MOM' 
FROM 
    resultado;
```

| DataFechamento | FaturamentoMM | desloc | %MOM     |
|----------------|---------------|--------|----------|
| 2019-10-01     | 24            | 24     | NULL     |
| 2019-11-01     | 30            | 24     | 25       |
| 2019-12-01     | 20            | 30     | -33.3333 |
| 2020-01-01     | 8             | 20     | -60      |
| 2020-02-01     | 10            | 8      | 25       |
| 2020-03-01     | 6             | 10     | -40      |
| 2020-04-01     | 9             | 6      | 50       |
| 2020-05-01     | 5             | 9      | -44.4444 |
| 2020-06-01     | 4             | 5      | -20      |
| 2020-07-01     | 7             | 4      | 75       |
| 2020-08-01     | 11            | 7      | 57.1429  |
| 2020-09-01     | 9             | 11     | -18.1818 |
| 2020-10-01     | 12            | 9      | 33.3333  |
| 2020-11-01     | 11            | 12     | -8.3333  |
| 2020-12-01     | 10            | 11     | -9.0909  |

***ánalise year-over-year (YOY)***

```sql
SELECT 
    *, 
    LAG(FaturamentoMM, 12, FaturamentoMM) OVER (ORDER BY DataFechamento) AS desloc,
    (FaturamentoMM / LAG(FaturamentoMM, 12, FaturamentoMM) OVER (ORDER BY DataFechamento) - 1 ) * 100 AS '%MOM' 
FROM 
    Resultado;

```
## 🟣 **STORED PROCEDURES**:

Uma stored procedure (procedimento armazenado) é um conjunto de instruções SQL pré-compiladas e armazenadas no banco de dados. Ela pode receber parâmetros, realizar operações complexas e retornar resultados. 

***criando procedure***
```sql


CREATE PROCEDURE nome_da_stored_procedure(
    -- Parâmetros (opcional)
    parametro1 tipo_de_dado,
    parametro2 tipo_de_dado
)
BEGIN
    -- Corpo da stored procedure
    -- Consultas, operações e lógica de negócios aqui

    -- Exemplo:
    SELECT coluna1, coluna2
    FROM tabela
    WHERE coluna1 = parametro1;

    -- Mais lógica, atualizações, etc.

END

```
exemplo de calculo de folha de pagamento
sem parâmetro

```sql


CREATE PROCEDURE CalcularFolhaPagamentoComDescontos()
BEGIN
    -- Variáveis para armazenar os valores dos descontos
    DECLARE IR DECIMAL(10, 2);
    DECLARE FGTS DECIMAL(10, 2);
    DECLARE INSS DECIMAL(10, 2);
    
    -- Calcular os descontos
    SET IR = 0.07;  -- 7% de IR
    SET FGTS = 0.08;  -- 8% de FGTS
    SET INSS = 0.09;  -- 9% de INSS

    -- Calcular o salário líquido para cada funcionário
    SELECT 
        nome, 
        departamento, 
        salario,
        salario - (salario * IR) - (salario * FGTS) - (salario * INSS) AS salario_liquido
    FROM Funcionarios;
END

```
resultado:

| Nome           | Departamento | Salário  | Salário Líquido |
|----------------|--------------|----------|-----------------|
| João Silva     | Vendas       | 3500.00  | 2660.00         |
| Maria Santos   | Marketing    | 4200.00  | 3192.00         |
| Pedro Oliveira | TI           | 5000.00  | 3800.00         |
| Ana Costa      | RH           | 3800.00  | 2888.00         |
| Carlos Mendes  | Financeiro   | 4600.00  | 3496.00         |

entretanto a procedure sem parâmetro não fica dinâmica.

com parâmetro:

```sql
CREATE PROCEDURE CalcularFolhaPagamentoComDescontos
    IN taxaIR DECIMAL(5,2),
    IN taxaFGTS DECIMAL(5,2),
    IN taxaINSS DECIMAL(5,2)
AS
BEGIN
    -- Calcular o salário líquido para cada funcionário
    SELECT 
        nome, 
        departamento, 
        salario,
        salario - (salario * taxaIR) - (salario * taxaFGTS) - (salario * taxaINSS) AS salario_liquido
    FROM Funcionarios;
END;

CALL CalcularFolhaPagamentoComDescontos(0.06, 0.08, 0.05);
```

resultado:

| Nome           | Departamento | Salário  | Salário Líquido |
|----------------|--------------|----------|-----------------|
| João Silva     | Vendas       | 3500.00  | 2835.00         |
| Maria Santos   | Marketing    | 4200.00  | 3402.00         |
| Pedro Oliveira | TI           | 5000.00  | 4050.00         |
| Ana Costa      | RH           | 3800.00  | 3078.00         |
| Carlos Mendes  | Financeiro   | 4600.00  | 3726.00         |

***chamando procedure***

```sql
CALL nome_da_stored_procedure(valor_parametro1, valor_parametro2);
```

***excluindo uma procedure***

```sql
DROP PROCEDURE IF EXISTS NomeProcedure;
```

***Ordem de comandos***

1. **SELECT**: Especifica quais colunas você deseja selecionar e pode incluir funções de agregação, como **`COUNT()`**, **`SUM()`**, **`AVG()`**, **`MIN()`**, **`MAX()`**, entre outras.

2. **FROM**: Especifica de qual tabela (ou tabelas) você está selecionando os dados.

3. **JOIN**: Une diferentes tabelas com base em uma condição de associação.

4. **WHERE**: Aplica condições para filtrar os dados.
5. **GROUP BY**: Agrupa os dados com base em uma ou mais colunas.

6. **HAVING**: Aplica condições de filtro a grupos criados pela cláusula **`GROUP BY`**.

7. **Funções condicionais**: Inclui funções condicionais, como **`CASE`**, **`IF`**, **`COALESCE`**, entre outras, que podem ser usadas para retornar valores condicionalmente com base em certas condições.

8. **ORDER BY**: Especifica a ordem de classificação dos resultados.

9. **LIMIT**: Limita o número de linhas retornadas pelo resultado.