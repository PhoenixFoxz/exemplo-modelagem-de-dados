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