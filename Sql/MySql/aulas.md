# Create a table

Para criar uma nova table:

CREATE TABLE nome_da_table (
    nome_da_coluna TIPO DE DADO,
    my_date DATE,
    my_time TIME,
    my_datetime DATETIME
)

# Alter the Table column name:

> Executar o script:

ALTER TABLE products
RENAME COLUMN Product_Name TO product_name;

# Insert some values on table

Para enserir manualmente um valor numa table:

INSERT INTO nome_da_tabela 
VALUES ("nome", 7, 7.9, "2032-05-11");


# Date value type

syntax:

date = "2025-02-17";

# Add a new table zone

ALTER TABLE nome_da_table
ADD phone VARCHAR(77);

# Set

UPDATE table
SET Row = NULL
WHERE id = 6;

> Altera na table o valor da Row onde(WHERE) id = 6; (Exemplo)

# Delete with Where

DELETE table
WHERE id = 6;

> Deleta uma row especifica da table pelo id;

# Auto-Commit 

No caso grave de erro em apagar dados no msql, É de suma importância o comando:

SET AUTOCOMMIT = OFF;

Desse modo nós iremos desativar o modo de salvamento automático das alterações, tendo que utilizar dois outros comandos:

COMMIT = Apos tuas alterações, é como um savestate, Onde para acessar o último "save" é necessário o comando ROLLBACK.


# Actual Date and times values:

> Esse script retorna a data atual mas, amanhã, um dia a frente:


INSERT INTO nome_da_table
VALUES (CURRENT_DATE() + 1, NULL, NULL);


> Esse retorna a atual:
data, horário e Hora-Data;

INSERT INTO nome_da_table
VALUES (CURRENT_DATE(), CURRENT_TIME(), NOW());

# Unique and NOT NULL command

> Comando colocado após o nome da coluna definida na table que define o tipo de dado é unico e não pode ser repetido, exemplo:

CREATE TABLE tables_name (
    nome VARCHAR(25) UNIQUE,
    preco DECIMAL(5, 2) NOT NULL
)

> Se esquecer de adicionar o UNIQUE em uma das colunas da TABLE, use o comando:

ALTER TABLE tables_name
ADD CONSTRAINT
UNIQUE (colummns_name);

> Ou

ALTER TABLE tables_name
MODIFY columns_name DECIMAL(5,2) NOT NULL

# CHECK RESTRICTION

> ADiciona uma restrição que será checada ao inserir de dados na coluna.

numa nova tabela seria algo como:

CREATE TABLE test(
    name  VARCHAR (50),
    age INT NOT NULL,
    plays_time DECIMAL (4, 2) NOT NULL
    CONSTRAINT chk_plays_time CHECK (plays_time >= 9.00)

    //"CONSTRAINT chk_plays_time" cria uma identifiação para a condição do CHECK
    // "chk" é abreviação de "CHECK" algo como "Check de horas jogadas"
)

> E para tables que já existem utilizasse:

ALTER TABLE tables_name 
ADD CONSTRAINT chk_plays_time CHECK (plays_time >= 9.00)

