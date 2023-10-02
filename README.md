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
