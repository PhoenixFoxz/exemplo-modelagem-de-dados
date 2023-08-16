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