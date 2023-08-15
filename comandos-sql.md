# Comandos SQL - Referências

## Modelagem Física com comandos DDL

### Criar banco de dados

```
CREATE DATABASE nome_banco CHARACTER SET utf8mb4;
```

### Criar tabela de fabricantes

```
CREATE TABLE nome_tabela(

    nome_campo1 INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome_campo2 VARCHAR(45) NOT NULL

);
```