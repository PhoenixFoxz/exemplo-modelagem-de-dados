# Comandos SQL - Referências

## Modelagem Física com comandos DDL

### Criar banco de dados

```SQL
CREATE DATABASE nome_banco CHARACTER SET utf8mb4;
```

### Criar a tabela fabricantes

```SQL
CREATE TABLE fabricantes(

    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL

);
```

### Vizualizar detalhes estruturais da tabela

```SQL
DESC fabricantes;
```

### Criar a tabela produtos

```SQL
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(500) NULL,
    preco DECIMAL(6,2) NOT NULL,
    fabricante_id INT NOT NULL
);
```

### Criação do relacionamento entre as tabelas (chave estrangeira)

```SQL
ALTER TABLE produtos 
    -- CONTRAINT/restrição indicando o nome do relacionamento
    ADD CONSTRAINT fk_produtos_fabricantes

    -- Criando a chave-estrangeira (fabricante_id) que
    -- aponta para a chave-primária (id) de outra tabela (fabricantes)
    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id);
```

### Exemplos de alterações estruturais na tabela

### Renomear tabela

```SQL
ALTER TABLE fabricantes RENAME TO fornecedores;
```

### Modificar colunas

```SQL
ALTER TABLE produtos
    MODIFY COLUMN preco INT NULL;

ALTER TABLE produtos
    MODIFY COLUMN preco DECIMAL(6,2) NOT NULL;
```

### Renomear colunas

```SQL
ALTER TABLE fabricantes
    CHANGE nome nome_do_fabricante VARCHAR(20) NOT NULL;

ALTER TABLE fabricantes
    CHANGE nome_do_fabricante nome VARCHAR(20) NOT NULL;
```