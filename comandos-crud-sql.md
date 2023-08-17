# Comandos para operações CRUD no Banco de dados

## Resumo

- C -> CREATE (Inserir dados usando comando 'INSERT')
- R -> READ (Ler dados usando comando 'SELECT')
- U -> UPDATE (Atualizar dados usando comando 'UPDATE')
- D -> DELETE (Excluir dados usando comando 'DELETE')

## INSERT

### Fabricantes

```SQL
INSERT INTO fabricantes (nome) VALUES('Asus'); 
INSERT INTO fabricantes (nome) VALUES('Dell'); 
INSERT INTO fabricantes (nome) VALUES('Apple'); 
INSERT INTO fabricantes (nome) 
VALUES('LG'), ('Samsung'), ('Brastemp'); 
INSERT INFO fabricantes (nome)
VALUE('Positivo'), ('Microsoft');
```

### Produtos

```SQL
INSERT INTO produtos(
    nome, preco, descricao, quantidade, fabricante_id) 
    VALUES(
        'Ultrabook', 
        3500,
        -- NULL ou '' para deixar vazio 
        'Equipamento de última feração cheio de recursos, com
        processador Intel core i9 do balacobaco',
        7,
        2 -- id do fabricante DELL
        -- Como já está colocada a chave estrangeira, deve-se usar o id
    );

INSERT INTO produtos(
    descricao, fabricante_id, nome, preco, quantidade)
    VALUE(
        'Tablet com a versão 14 do sistema operacional Android,
        possui tela de 10 polegadas e armazenamento de 128 GB,
        e 64 GB de RAM porque o Eliel perguntou.',
        5,
        'Tablet Android',
        1500.99,
        5
    )

INSERT INTO produtos(
    descricao, fabricante_id, nome, preco, quantidade)
    VALUE(
        'Refrigerador frost-free com acesso à internet',
        6,
        'Geladeira',
        5000,
        12
    ), (
        'Smartphone Apple cheio das frescuras e caro para caramba. Coisa de rico...',
        3,
        'iPhone 18 pro Max',
        12666.66,
        3,
    ), (
        'Tablet Apple com tela retina display e bla bla bla',
        3,
        'iPad Mini',
        4999.01,
        5,
    );
```

## SELECT

```SQL
SELECT * FROM produtos;

SELECT nome, preco FROM produtos;

-- A ordem das colunas, altera na saída

SELECT preco, nome FROM produtos;

-- Condição perando a motra de dados
SELECT nome, preco, quantidade FROM produtos WHERE preco < 5000;

-- Mostre nome e descrição somente dos produtos da Apple
SELECT nome, descricao FROM produtos WHERE fabricante_id = 3; -- Id do fabricante Apple
```

### Operadores Lógicos: E, OU, NÃO

```SQL
SELECT nome, preco FROM produtos WHERE preco >= 2000 AND preco <= 6000;

-- A query abaixo não retorna registros
-- já que as condições não foram totalmente atendidas
SELECT nome, preco FROM produtos WHERE preco > 5000 AND preco <= 6000;
```

**OU**

```SQL
SELECT nome, preco FROM produtos WHERE preco > 5000 OR preco <= 3000;

-- Exiba nome e preco somente dos produtos da Apple e da Samsung
SELECT nome, preco FROM produtos WHERE fabricante_id = 3 OR fabricante_id = 5;

-- Versão usando a função IN()
SELECT nome, preco FROM produtos WHERE fabricante_id IN(3, 5);

-- Versão invertendo a lógica da função
SELECT nome, preco FROM produtos WHERE fabricante_id NOT IN(3, 5);
```

**NÃO**

```SQL
SELECT nome, descricao, preco FROM produtos WHERE NOT fabricante_id = 8;

-- Versão usando operador relacional "diferença/diferente"
SELECT nome, descricao, preco FROM produtos WHERE fabricante_id != 8;
```

## UPDATE

```SQL
UPDATE fabricantes SET nome = 'Asus do Brasil' WHERE id = 1; -- NÃO SE ESQUEÇA DO WHERE!! PRERIGO!

UPDATE fabricantes_zueira SET nome = 'Asus do Paraguai';

UPDATE produtos SET preco = 6549.74 WHERE id = 4;

UPDATE produtos SET quantidade = 20 WHERE fabricante_id = 3 OR fabricante_id = 5;
```

## DELETE

```SQL
-- NÃO SE ESQUEÇA DO WHERE!! PRERIGO!
DELETE FROM fabricantes WHERE id = 1;
DELETE FROM fabricantes WHERE id = 4;

-- A query abaixo NÃO FUNCIONA devido à restrição de chave estrangeira/relacionamento, ou seja, existem produtos associados ao fabricante 3 (Apple) 
DELETE FROM fabricantes WHERE id = 3;
```

## SELECT: outras formas de uso

### Classificando

```SQL
SELECT nome, preco FROM produtos ORDER BY nome;
SELECT nome, preco FROM produtos ORDER BY preco;
SELECT nome, preco FROM produtos ORDER BY preco DESC;

-- DESC: classificação em ordem decrescente
-- ASC (padrão): classificação em ordem crescente 

SELECT nome, preco FROM produtos WHERE quantidade = 20 ORDER BY nome;
```

### Busca de dados

```SQL
SELECT nome, descricao FROM produtos WHERE descricao LIKE '%tablet%';
SELECT nome, descricao FROM produtos WHERE descricao LIKE '%tablet%' OR nome LIKE '%tela%';

-- Usamos o operador LIKE e o caractere corinha % para permitir uma busca da palavra indicada em qualquer posição dentro do texto. Nesse contexto, o % significa 'qualquer texto' antes da palavra ou depois da palavra
```

### Operações e funções de agregação

```SQL
SELECT SUM(preco) FROM produtos; -- SOMA
SELECT SUM(preco) as Total FROM produtos; -- alias/apelido

-- Exemplo de alias/apelido para outras colunas
SELECT nome as Produto, preco as Preço FROM produtos;
SELECT nome Produto, preco Preço FROM produtos;

-- MÉDIA E ARREDONDAMENTO
SELECT AVG(preco) as "Média dos Preços" FROM produtos;
SELECT ROUND(AVG(preco)) as "Média dos Preços" FROM produtos;
SELECT ROUND(AVG(preco), 2) as "Média dos Preços" FROM produtos;

-- CONTAGEM
SELECT COUNT(id) as "Qtd de Produtos" FROM produtos;
SELECT COUNT(fabricante_id) as "Qtd de Fabricantes com Produtos" FROM produtos;

-- DISTINCT: Evita a contagem de itens repitidos
SELECT COUNT(DISTINCT fabricante_id) as "Qtd de Fabricantes com Produtos" FROM produtos;

-- DISTINCT é uma cláusula/flag que evita a duplicidade na contagem de registros.
```

### Operações matemáticas

```SQL
SELECT nome, preco, quantidade, (preco * quantidade) as Total FROM produtos;
```

### Segmentação/Agrupamento de resultados

```SQL
UPDATE produtos SET fabricante_id = 2 WHERE id = 2;
SELECT fabricante_id, SUM(preco) FROM produtos;
SELECT fabricante_id, SUM(preco) FROM produtos GROUP BY fabricante_id;
SELECT fabricante_id, SUM(preco) as Total FROM produtos GROUP BY fabricante_id;
```

