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

-- exer 2

CREATE TABLE produtos (
    produto VARCHAR(50),
    preco DECIMAL(10, 2),
    quantidade INT
); 



SELECT produto, preco, ABS(quantidade) AS quantidade_absoluta
FROM produtos;

SELECT AVG(preco) AS media_precos
FROM produtos;


-- exer 3

CREATE TABLE eventos (
    data_evento DATE
);

INSERT INTO eventos (data_evento)
VALUES (NOW());

SELECT data_evento, DAYNAME(data_evento) AS nome_dia_semana
FROM eventos;

-- exer 4

select
  produto, preco, quantidade,
  if(quantidade > 0, 'Em estoque', 'Fora de estoque') as estoque
from produtos;

select
  produto, preco, quantidade,
  case
    when preco < 40.00 then 'Barato'
    when preco >= 40.00 and preco < 100.00 then 'Médio'
    else 'Caro'
  end as categoria
from produtos;


