# CP2

## Print da tela do WebApp (com o link) rodando com o resultado do CSV.

<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/7c0c63f6-944a-41d9-8926-b96dfa224203" />


## Script SQL com as tabelas do banco.

```
CREATE TABLE Instrutores (
    Id INT PRIMARY KEY IDENTITY(1,1),
    NomeCompleto VARCHAR(150) NOT NULL,
    Email VARCHAR(100) UNIQUE NOT NULL,
	DataNascimento DATE NOT NULL
);

CREATE TABLE Cursos (
    Id INT PRIMARY KEY IDENTITY(1,1),
    NomeCurso VARCHAR(200) NOT NULL,
    CargaHoraria INT NOT NULL,
    Valor DECIMAL(10, 2) NOT NULL
);

CREATE TABLE Alunos (
    Id INT PRIMARY KEY IDENTITY(1,1),
    NomeCompleto VARCHAR(150) NOT NULL,
    Email VARCHAR(100) UNIQUE NOT NULL,
    DataNascimento DATE NOT NULL
);

CREATE TABLE CursoInstrutor (
    CursoID INT NOT NULL,
    InstrutorID INT NOT NULL,
    
    CONSTRAINT PK_CursoInstrutor PRIMARY KEY (CursoID, InstrutorID),

    CONSTRAINT FK_CursoInstrutor_Cursos FOREIGN KEY (CursoID) REFERENCES Cursos(Id),
    CONSTRAINT FK_CursoInstrutor_Instrutores FOREIGN KEY (InstrutorID) REFERENCES Instrutores(Id)
);

CREATE TABLE Inscricoes (
    InscricaoID INT PRIMARY KEY IDENTITY(1,1),
    AlunoID INT NOT NULL,
    CursoID INT NOT NULL,
    DataInscricao DATETIME DEFAULT GETDATE(),
    StatusInscricao VARCHAR(20) NOT NULL DEFAULT 'Ativa',
    NotaFinal DECIMAL(4, 2) NULL,

    CONSTRAINT UQ_Aluno_Curso UNIQUE (AlunoID, CursoID), 
    
    CONSTRAINT FK_Inscricoes_Alunos FOREIGN KEY (AlunoID) REFERENCES Alunos(Id),
    CONSTRAINT FK_Inscricoes_Cursos FOREIGN KEY (CursoID) REFERENCES Cursos(Id)
);


INSERT INTO Instrutores (NomeCompleto, Email, DataNascimento) VALUES
('Rodrigo Alves', 'rodrigo.a@example.com', '1988-07-15'),
('Juliana Lima', 'juliana.l@example.com', '1992-02-20');

INSERT INTO Cursos (NomeCurso, CargaHoraria, Valor) VALUES
('Banco de Dados SQL: Do Básico ao Avançado', 80, 550.00),
('Desenvolvimento Web com React', 120, 799.90),
('Machine Learning com Python', 100, 650.00);

INSERT INTO Alunos (NomeCompleto, Email, DataNascimento) VALUES
('Fernanda Oliveira', 'fernanda.o@email.com', '2003-04-12'),
('Gabriel Santos', 'gabriel.s@email.com', '2001-09-05'),
('Mariana Costa', 'mariana.c@email.com', '2004-01-25');

INSERT INTO CursoInstrutor (CursoID, InstrutorID) VALUES
(1, 1),
(2, 2),
(3, 2);

INSERT INTO Inscricoes (AlunoID, CursoID, StatusInscricao) VALUES
(1, 1, 'Ativa'),
(2, 2, 'Ativa'),
(3, 1, 'Ativa'),
(1, 3, 'Concluída');


SELECT
    I.InscricaoID,
    I.DataInscricao,
    I.StatusInscricao,
    I.NotaFinal,

    A.Id AS AlunoId,
    A.NomeCompleto AS AlunoNome,
    A.Email AS AlunoEmail,
    A.DataNascimento AS AlunoDataNascimento,

    C.Id AS CursoId,
    C.NomeCurso,
    C.CargaHoraria,
    C.Valor AS ValorCurso,

    INS.Id AS InstrutorId,
    INS.NomeCompleto AS InstrutorNome,
    INS.Email AS InstrutorEmail,
    INS.DataNascimento AS InstrutorDataNascimento
FROM
    Inscricoes AS I
JOIN Alunos AS A ON I.AlunoID = A.Id
JOIN Cursos AS C ON I.CursoID = C.Id
JOIN CursoInstrutor AS CI ON C.Id = CI.CursoID
JOIN Instrutores AS INS ON CI.InstrutorID = INS.Id
ORDER BY
    I.InscricaoID;
 ```

## Print do recurso Azure SQL Database criado.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9c4165d0-e6b5-4dcf-be42-d26f0e6a0d59" />

## Print do Azure Monitor ativo no WebApp.
<img width="2485" height="1184" alt="image" src="https://github.com/user-attachments/assets/b3764ce5-bfd4-4883-9576-19719e8f0ee6" />

<img width="1775" height="1003" alt="image" src="https://github.com/user-attachments/assets/d5a9fcac-8024-425f-89b9-0700a04eb4ee" />

## Print da regra de alerta configurada para HTTP 404 e a notificação recebida.
<img width="2155" height="1079" alt="image" src="https://github.com/user-attachments/assets/4ef23e6b-8797-41c6-978b-d0ccb2c327ef" />


## Link do Projeto no Boards

## Print do Backlog (com heranças)
