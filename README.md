# uber
Projeto uber


CREATE TABLE motorista (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
  	cpf TEXT NOT NULL UNIQUE,
	email TEXT NOT NULL,
	endereco TEXT NOT NULL,
	celular TEXT NOT NULL,
  	marca TEXT NOT NULL,
 	placa TEXT NOT NULL,
  	cor TEXT NOT NULL,
);


CREATE TABLE corrida (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
  	local_partida NOT NULL,
  	destino_final NOT NULL,
  	valor REAL NOT NULL DEFAULT 0.00,
    data_criacao DATETIME NOT NULL DEFAULT (datetime('now','localtime'))
);

CREATE TABLE cliente (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
	nome TEXT NOT NULL,
	cpf TEXT NOT NULL UNIQUE,
	celular TEXT NOT NULL
	email TEXT NOT NULL,

);

CREATE TABLE pagamento (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
	debito ativo BOOLEAN DEFAULT TRUE,
	credito ativo BOOLEAN DEFAULT TRUE,
	pix ativo BOOLEAN DEFAULT TRUE,
	dinheiro ativo BOOLEAN DEFAULT TRUE,

);


CREATE TABLE uber (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    id_motorista INTEGER NOT NULL,
    id_corrida INTEGER NOT NULL,
    id_pagamento INTEGER NOT NULL,
    id_cliente INTEGER NOT NULL,
    marca_de_carro TEXT NOT NULL,
    placa_de_crro TEXT NOT NULL,
    cor_de_carro TEXT NOT NULL
  	FOREIGN KEY(id_motorista) REFERENCES motorista(id),
  	FOREIGN KEY(id_corrida) REFERENCES corrida(id),
  	FOREIGN KEY(id_pagamento) REFERENCES pagamento(id),
  	FOREIGN KEY(id_cliente) REFERENCES cliente(id),
);



select * from cliente;
select * from motorista;
select * from pagamento;
select * from corrida;
select * from uber;


INSERT INTO motorista (nome,cpf,email,endereco,celular,marca,placa,cor) VALUES ('JOAO DA SILVA''23660628740','joao@gmail.com','RUA DOS PROGRAMADORES 20','119879497330','Chevrolet','CH0214','vermelha');

INSERT INTO motorista (nome,cpf,email,endereco,celular,marca,placa,cor) VALUES ('HELENA SILVA''55660628740','hme@gmail.com','RUA VERMELHA 200','119866697330','Chevrolet','WR1515','Branco');

INSERT INTO motorista (nome,cpf,email,endereco,celular,marca,placa,cor) VALUES ('NADINE CARVALHO''55687428740','brac@gmail.com','AV DAS NACOES 100','149866697330','Citroën','RC1589','Preto');

select * from motorista;

/* selecionar todos da tabela motorista */
 
 SELECT id, nome FROM motorista WHERE id = 3;

/*selecione o id e o nome da motorista cujo o id é igual número 3*/

SELECT id, nome FROM motorista WHERE nome LIKE ‘JOAO%’;

/* retornar os nomes que contenham ‘JOAO’ também no meio */



/* inserir os dados na tabela corrida */

INSERT INTO corrida (local_partida,destino_final,valor,data) VALUES
('Rua das arvores 12','av 5 de julio 433','25,00','20-03-2022');

INSERT INTO corrida (local_partida,destino_final,valor,data) VALUES
('Rua das arvores 102','Rua Azul 45','100,00','02-03-2022');

INSERT INTO corrida (local_partida,destino_final,valor,data) VALUES
('Rua 14 de novembro 1818','Rau jose cristo','50,00','10-03-2022');


SELECT id_cliente, COUNT(*)
FROM corrida
WHERE DATA > '02-30-2022'
GROUPY BY id_cliente
HAVING COUNT(*) >= 2;


/* selecionar somente os clientes com 2 ou mais pedidos serão selecionados*/


SELECT id_cliente, COUNT(*)
FROM corrida
WHERE DATA > '10-03-2022'
GROUPY BY id_cliente
HAVING COUNT(*) >= 2;
 /* selecionar as datas maior que 10-03-2022. */
 
 
 
 
 /* inserir os dados na tabela cliente */
 INSERT INTO cliente (nome,cpf,celular,email) VALUES
('MARCOS VELHO','23569854721','15-98745689952','velho91@hotmail.com');

INSERT INTO cliente (nome,cpf,celular,email) VALUES
('MARIA DO SANTOS','58769854721','12-99745689952','joo@hotmail.com');

INSERT INTO cliente (nome,cpf,celular,email) VALUES
('MARCIA COSTA','3659987524182','11-98745759442','vasco@hotmail.com');

INSERT INTO cliente (nome,cpf,celular,email) VALUES
('paula ferreira','25478854721','11-98745875152','cletnovida@gmail.com');

select * from cliente;
/*listar todos da tabela cliente*/

SELECT id, nome FROM cliente
UNION
SELECT id. motorista FROM motorista;

/*junção das duas tabelas pelo ids*/


/* inserir os dados na tabela pagamento*/

INSERT INTO pagamento (debito,credito,pix,dimheiro) VALUES
('credito','x','x','x);

INSERT INTO pagamento (debito,credito,pix,dimheiro) VALUES
('dinheiro','x','x','x);

INSERT INTO pagamento (debito,credito,pix,dimheiro) VALUES
('pix','x','x','x);
 
 INSERT INTO pagamento (debito,credito,pix,dimheiro) VALUES
('debito','x','x','x);


SELECT id, nome FROM pagamento
WHERE id = debito;

/*selecionar id e nome na tabela pagamento onde o pagamento foi debito*/

SELECT id, nome FROM pagamento
WHERE id >= 1 AND id <= 3;



/* inserir os dados na tabela UBER*/

INSERT INTO uber (marca,placa,cor) VALUES('Chevrolet','CH5874','BRANCO');

INSERT INTO uber (marca,placa,cor) VALUES('Citroën','SA74','PRETO');

INSERT INTO uber (marca,placa,cor) VALUES('Ford','C2J74','CINZA');

INSERT INTO uber (marca,placa,cor) VALUES('Nissan','6587','PRETO');








