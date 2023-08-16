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

```