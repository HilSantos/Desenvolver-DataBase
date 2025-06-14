-- Criação do banco de dados --
CREATE DATABASE School;
USE School;

-- Criação da tabela Cursos --
CREATE TABLE Cursos (
  id_Curso INT AUTO_INCREMENT PRIMARY KEY,
  name_Curso VARCHAR(50) NOT NULL,
  name_teacher VARCHAR(50) NOT NULL
);

-- Criação da tabela Students --
CREATE TABLE Students (
  id_int INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(35) NOT NULL,
  materia VARCHAR(50) NOT NULL,
  Cursos_id INT,
  FOREIGN KEY (Cursos_id) REFERENCES Cursos(id_Curso)
);

-- Inserção de cursos --
INSERT INTO Cursos (name_Curso, name_teacher) VALUES
('Biotecnologia', 'Prof. Silva'),
('Meio Ambiente e Sustentabilidade', 'Prof. Souza'),
('Energias Renováveis', 'Prof. Lima');

-- Inserção de estudantes --
INSERT INTO Students (name, materia, Cursos_id) VALUES
('João Carlos', 'Biotecnologia', 1),
('José Vitor', 'Meio Ambiente e Sustentabilidade', 2),
('Paulo André', 'Energias Renováveis', 3);

-- Consultas de junção --
-- Inner join --
SELECT c.name_Curso AS cursos_nome, s.name AS nome
FROM Cursos c
INNER JOIN Students s ON s.Cursos_id = c.id_Curso;

-- Left join --
SELECT c.name_Curso AS cursos_nome, s.name AS nome
FROM Cursos c
LEFT JOIN Students s ON s.Cursos_id = c.id_Curso;

-- Right join (não suportado por alguns SGBDs como MySQL sem especificar o tipo de tabela) --
SELECT c.name_Curso AS cursos_nome, s.name AS nome
FROM Cursos c
RIGHT JOIN Students s ON s.Cursos_id = c.id_Curso;

-- Union das junções --
SELECT c.name_Curso AS cursos_nome, s.name AS nome
FROM Cursos c
LEFT JOIN Students s ON s.Cursos_id = c.id_Curso
UNION
SELECT c.name_Curso AS cursos_nome, s.name AS nome
FROM Cursos c
RIGHT JOIN Students s ON s.Cursos_id = c.id_Curso;
