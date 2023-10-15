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


-- exer 5

delimiter //
create function total_valor(preco decimal(10, 2), quantidade int) returns decimal(10, 2) deterministic
begin
declare va_total decimal(10, 2);
set v_total = preco * quantidade;
return va_total;
end;
// 
delimiter ;

select total_valor(49.70, 20) as total;
select total_valor(239.9999, 200) as total;
select total_valor (28.9999, 50) as total;
select total_valor (81.9999, 100) as total;
select total_valor (17.9999, 120) as total;

-- exer 6

select count(produto) as total from produtos;


select produto, preco
from produtos
where preco = (select max(preco) from produtos);


select produto, preco
from produtos
where preco = (select min(preco) from produtos);


select sum(if(quantidade > 0, preco * quantidade, 0)) as soma
from produtos;

