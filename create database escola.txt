create database Escola;


create table Funcionarios(
id_funcionario int primary key auto_increment,
nome_funcionarios varchar(30),
cargo varchar(15),
contato_funcionarios varchar(15));

create table Turma(
id_turma int primary key auto_increment,
ano_sala varchar(20),
num_sala int,
num_alunos int,
id_funcionario int,
foreign key(id_funcionario) references funcionarios(id_funcionario));

create table alunos(
id_alunos int primary key auto_increment,
nome_aluno varchar(30),
id_turma int,
cidade varchar(25),
foreign key(id_turma) references Turma(id_turma));

create table cantina(
id_produtos int primary key auto_increment,
nome_produto varchar(20),
estoque int,
preco decimal (15, 2));

create table responsaveis(
id_responsavel int primary key auto_increment,
nome_responsavel varchar(30),
contato_responsavel varchar(15),
id_alunos int,
cidade varchar(25),
foreign key(id_alunos) references Alunos(id_alunos));

insert into funcionarios(nome_funcionarios, cargo, contato_funcionarios) values 
("Joselma Candida Santos","Cantina", "11-111111-1111"),
("José Augusto Rodrigues","Professor", "19-9999999-1919"),
("Sivaldo Arruda Rocha","Professor", "19-9999999-1919");

insert into turma(ano_sala, num_sala, num_alunos, id_funcionario) values
("1º ano medio", "2", "35", 02),
("7º ano fundamental","6", "31",02),
("3º ano medio", "9", "38",03);

insert into alunos(nome_aluno, cidade, id_turma) values
('Enzo Junior Costa',"Itu",01),
('Pedro Cabral Mendes',"Salto", 02),
('Julia Ribeiro Castro',"Indaiatuba", 03);


insert into cantina(nome_produto, preco, estoque) values 
("Coca-Cola 250 ml", "5,00", "25"),
("Pirulito POP", "1,00", "110"),
("Hambuerguer", "8,50", "10");

insert into responsaveis(nome_responsavel, contato_responsavel, cidade, id_alunos) values
("Fabio De Souza", "15-191919-1008","Itu", 01),
("Maria Oliveira Santos", "12-122231-2312","Indaiatuba",03),
("Walter Costa Ramos", "10-101999-0001","Salto", 02);


select nome_aluno
from Alunos;

select nome_responsavel, cidade
from Responsaveis;

select preco, estoque
from Cantina;

SELECT
	r.nome_responsavel, r.contato_responsavel, r.cidade, a.nome_aluno 
FROM Responsaveis r
INNER JOIN Alunos a ON r.id_alunos = a.id_alunos;
	
SELECT
	a.nome_aluno, a.cidade,  t.num_sala 
FROM alunos a
INNER JOIN turma t ON a.id_alunos = t.id_alunos;

SELECT
	t.ano_sala, t.num_sala, t.num_alunos, f.nome_funcionarios 
FROM turma t
INNER JOIN funcionarios f ON t.id_funcionario = f.id_funcionario;

update alunos
set nome_aluno = "Rafael Leão" where id_alunos = 1;

update cantina
set preco = "6,00" where id_produtos = "3";

update cantina
set estoque = "36" where id_produtos ="1";

SELECT id_produtos, nome_produto, estoque, preco FROM cantina WHERE preco = (SELECT MAX(preco) FROM cantina);

SELECT id_produtos, nome_produto, estoque, preco FROM cantina WHERE preco = (SELECT MIN(preco) FROM cantina);

ALTER TABLE alunos add idade int (3);

ALTER TABLE funcionarios add email varchar(30);

ALTER TABLE responsaveis add email varchar(30);

DELETE FROM cantina where estoque = "36";

DELETE FROM funcionario where id_funcionario = "1";


