# banco-de-dados-FUNCOES

CREATE TABLE nomes (
    nome VARCHAR(50)
);

INSERT INTO nomes (nome)
VALUES
    ('Roberta'),
    ('Roberto'),
    ('Maria Clara'),
    ('João');

SELECT UPPER(nome) AS nome_maiusculo
FROM nomes;    
SELECT nome, LENGTH(nome) AS tamanho
FROM nomes;
SELECT CASE 
WHEN nome LIKE '%a' THEN CONCAT('Sra. ', nome)
ELSE CONCAT('Sr. ', nome)
END AS tratamento
FROM nomes;

CREATE TABLE produtos (
    produto VARCHAR(50),
    preco DECIMAL(10, 2),
    quantidade INT
); 

SELECT produto, preco, ABS(quantidade) AS quantidade_absoluta
FROM produtos;

SELECT AVG(preco) AS media_precos
FROM produtos;


