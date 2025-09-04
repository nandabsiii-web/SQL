CREATE DATABASE empresa;
USE empresa;

CREATE TABLE funcionarios
(
	id int unsigned not null auto_increment,
    nome varchar(45) not null,
    salario double not null default 0,
    departamento varchar(45) not null,
    PRIMARY KEY (id)
    );
    
    ALTER TABLE funcionarios
ADD faixa VARCHAR(45) NOT NULL,
ADD CONSTRAINT fk_funcionarios_salarios
    FOREIGN KEY (faixa) REFERENCES salarios(faixa);
    
    
CREATE TABLE veiculosfuncionarios
(
	id int unsigned not null auto_increment,
    funcionario_id int unsigned default null,
    veiculo varchar(45) not null default '',
    placa varchar (10) not null default '',
	primary key (id),
    CONSTRAINT fk_veiculos_funcionarios foreign key(funcionario_id) REFERENCES funcionarios (id)
    );
    
CREATE TABLE salarios
(
	faixa varchar(45) not null,
    inicio double not null,
    fim double not null,
    PRIMARY KEY (faixa)
    );
INSERT INTO salarios (faixa, inicio, fim) VALUES
('Júnior', 2000, 4000),
('Pleno', 4001, 7000),
('Sênior', 7001, 12000);
    
INSERT INTO funcionarios (nome, salario, departamento, faixa) VALUES
('MARIA CLARA', 3500, 'PESSOAL','Júnior'),
('JOANA', 2000, 'FINANCEIRO','Júnior'),
('LUCAS', 2500, 'MKT','Júnior');

SELECT f.nome, f.salario, f.departamento, s.faixa, s.inicio, s.fim
FROM funcionarios f
JOIN salarios s ON f.faixa = s.faixa;

