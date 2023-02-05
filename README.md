# Desenvolver-DataBase

CREATE DATABASE School(

use School;

CREATE TABLE Students(

PRIMARY KEY (ID_INT),

id_int not null auto_increment,

name VARCHAR(35) not null,

materia VARCHAR(50) not null,

Cursos_id INT,

CONSTRAINT FOREIGN KEY (Cursos_id)

REFERENCES Cursos (id_Curso)

);

insert into Students(name, materia) values('João Carlos', Biotecnologia),
('José Vitor', Meio Ambiente e Sustentabilidade),
('Paulo André', Energias Renovaveis);

select * from Students;

CREATE TABLE Cursos(

id_Curso int AUTO_INCREMENT PRIMARY KEY,

name_Curso VARCHAR(50) not null,

name_teacher VARCHAR(50) not null,

);

select * from Cursos;
________________________________________________________________________
select cursos_nome, nome

from cursos inner join students

on students.id_cli = cursos.cli_id;
________________________________________________________________________
select cursos_nome, nome

from cursos left join students

on students.id_cli = cursos.cli_id;
________________________________________________________________________
select cursos_nome, nome

from cursos right join students

on students.id_cli = cursos.cli_id;
________________________________________________________________________
select cursos_nome, nome

from cursos left join students

on students.id_cli = cursos.cli_id

union

select cursos_nome, nome

from cursos right join students

on students.id_cli = cursos.cli_id;

