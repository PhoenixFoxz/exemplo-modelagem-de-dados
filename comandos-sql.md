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