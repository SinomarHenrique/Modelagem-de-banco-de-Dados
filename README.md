# Sistema de Gestão de Escola de Idiomas

## Cenário

Descrição do sistema e suas necessidades:
- Uma escola de idiomas deseja um sistema para gerenciar seus alunos, professores, cursos, matrículas e turmas. Os alunos podem se matricular em diversos cursos oferecidos pela escola. Cada matrícula registra informações como dados de matrícula, situação de pagamento, valor de pagamento e pendente.

Cada curso possui várias turmas, com diferentes horários e dias da semana. Um curso pode ser oferecido em turmas presenciais, online ou semi-presenciais. Cada turma tem uma capacidade máxima de alunos, e o sistema deve manter o controle do número de alunos matriculados em cada turma.

Os professores são responsáveis ​​por ministrar as aulas nas turmas. Cada professor pode ser designado para várias turmas, mas cada turma é ministrada por apenas um professor.

O sistema também deve calcular o nível de proficiência dos alunos com base em seu desempenho nas aulas e nas avaliações, fornecendo insights sobre o progresso de cada aluno.

Essa estrutura permite à escola de idiomas gerenciar eficientemente suas operações, desde o cadastro de alunos e professores até o controle de matrículas, turmas e cursos oferecidos, garantindo uma experiência organizada e eficaz para alunos e funcionários.

## Modelagem Conceitual

![Modelagem de banco de dados completa - Sinomar-2_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/201afbad-ccd8-4469-a7ae-2ef1cfbbce16)


A modelagem conceitual é uma representação abstrata das entidades, atributos e relacionamentos em um sistema. Ela ajuda a visualizar a estrutura do banco de dados de uma forma mais simplificada e compreensível.

### Modelagem Conceitual:

No contexto do sistema de gestão da escola de idiomas, temos várias entidades inter-relacionadas:

#### Entidades Principais:

1. **Aluno:**
   - **Atributos:**
     - ID_aluno (Chave primária)
     - Nome
     - Endereço
     - E-mail
     - Telefone
     - Data de matrícula
     - Nível de proficiência

2. **Professor:**
   - **Atributos:**
     - ID_professor (Chave primária)
     - Nome
     - Endereço
     - E-mail
     - Telefone
     - Salário
     - Data de contratação

3. **Curso:**
   - **Atributos:**
     - ID_curso (Chave primária)
     - Nome do curso
     - Descrição do curso
     - Carga horária
     - Valor do curso
     - Tipo de curso (presencial, online, semi-presencial)

4. **Matrícula:**
   - **Atributos:**
     - ID_matrícula (Chave primária)
     - Data de matrícula
     - Status de pagamento
     - Valor pago
     - Valor pendente

5. **Turma:**
   - **Atributos:**
     - ID_turma (Chave primária)
     - Horário da turma
     - Dia da semana
     - Capacidade máxima
     - Número de alunos matriculados

#### Relacionamentos:

- **Aluno - Matrícula (N:N):** Um aluno pode ter várias matrículas, e uma matrícula pode incluir vários alunos.
- **Curso - Matrícula (1:N):** Um curso pode ter várias matrículas, mas uma matrícula está associada a apenas um curso.
- **Curso - Turma (1:N):** Um curso pode ter várias turmas, mas uma turma está associada a apenas um curso.
- **Professor - Turma (1:N):** Um professor pode ministrar várias turmas, mas uma turma é ministrada por apenas um professor.

Essa representação simplificada mostra as entidades (Aluno, Professor, Curso, Matrícula e Turma), seus atributos e como elas se relacionam no contexto do sistema de gestão da escola de idiomas. Essa visão é fundamental para entender a estrutura do banco de dados e como os dados estão interligados.

## Modelagem Lógica
![Modelagem de banco de dados completa - Sinomar-3_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/5b8fcaa3-dabc-46fd-b82f-74f0ac7c2d2f)

### Tabelas do Banco de Dados:

#### Tabela Aluno:

- **Atributos:**
  - ID_aluno (Chave primária)
  - Nome
  - Endereço
  - E-mail
  - Telefone
  - Data de matrícula
  - Nível de proficiência

- **Relacionamentos:**
  - Relacionamento N:N com a tabela Matrícula através da chave estrangeira ID_aluno.

#### Tabela Professor:

- **Atributos:**
  - ID_professor (Chave primária)
  - Nome
  - Endereço
  - E-mail
  - Telefone
  - Salário
  - Data de contratação

- **Relacionamentos:**
  - Relacionamento 1:N com a tabela Turma através da chave estrangeira ID_professor.

#### Tabela Curso:

- **Atributos:**
  - ID_curso (Chave primária)
  - Nome do curso
  - Descrição do curso
  - Carga horária
  - Valor do curso
  - Tipo de curso (presencial, online, semi-presencial)

- **Relacionamentos:**
  - Relacionamento 1:N com a tabela Matrícula através da chave estrangeira ID_curso.
  - Relacionamento 1:N com a tabela Turma através da chave estrangeira ID_curso.

#### Tabela Matrícula:

- **Atributos:**
  - ID_matrícula (Chave primária)
  - Data de matrícula
  - Status de pagamento
  - Valor pago
  - Valor pendente

- **Relacionamentos:**
  - Relacionamento N:1 com a tabela Aluno através da chave estrangeira ID_aluno.
  - Relacionamento N:1 com a tabela Curso através da chave estrangeira ID_curso.

#### Tabela Turma:

- **Atributos:**
  - ID_turma (Chave primária)
  - Horário da turma
  - Dia da semana
  - Capacidade máxima
  - Número de alunos matriculados (pode ser um atributo derivado)

- **Relacionamentos:**
  - Relacionamento 1:N com a tabela Curso através da chave estrangeira ID_curso.
  - Relacionamento 1:N com a tabela Professor através da chave estrangeira ID_professor.
  
Essas descrições detalhadas apresentam os atributos de cada tabela, suas chaves primárias, e os relacionamentos entre elas, fornecendo uma visão abrangente da estrutura lógica do banco de dados para o sistema de gestão da escola de idiomas.


## Dados

### Inserção de Dados no Banco

-- Tabela Aluno

CREATE TABLE Aluno (

    ID_aluno INT PRIMARY KEY,
    
    Nome VARCHAR(100),
    
    Endereco_rua VARCHAR(100),
    
    Endereco_cidade VARCHAR(50),
    
    Endereco_estado VARCHAR(50),
    
    Endereco_CEP VARCHAR(10),
    
    Email VARCHAR(100),
    
    Telefone_celular VARCHAR(20),
    
    Telefone_residencial VARCHAR(20),
    
    Data_de_matricula DATE,
    
    Nivel_de_proficiencia VARCHAR(50)
 
 );

-- Tabela Professor

CREATE TABLE Professor (
    
    ID_professor INT PRIMARY KEY,
    
    Nome VARCHAR(100),
    
    Endereco_rua VARCHAR(100),
    
    Endereco_cidade VARCHAR(50),
    
    Endereco_estado VARCHAR(50),
    
    Endereco_CEP VARCHAR(10),
    
    Email VARCHAR(100),
    
    Telefone_celular VARCHAR(20),
    
    Telefone_residencial VARCHAR(20),
    
    Salario DECIMAL(10, 2),
    
    Data_de_contratacao DATE

);

-- Tabela Curso

CREATE TABLE Curso (
    
    ID_curso INT PRIMARY KEY,
    
    Nome_do_curso VARCHAR(100),
    
    Descricao_do_curso TEXT,
    
    Carga_horaria INT,
    
    Valor_do_curso DECIMAL(10, 2),
    
    Tipo_de_curso VARCHAR(50)

);

-- Tabela Matricula

CREATE TABLE Matricula (
    
    ID_matricula INT PRIMARY KEY,
    
    ID_aluno INT,
    
    ID_curso INT,
    
    Data_de_matricula DATE,
    
    Status_de_pagamento VARCHAR(50),
    
    Valor_pago DECIMAL(10, 2),
    
    Valor_pendente DECIMAL(10, 2),
    
    FOREIGN KEY (ID_aluno) REFERENCES Aluno(ID_aluno),
    
    FOREIGN KEY (ID_curso) REFERENCES Curso(ID_curso)

);

-- Tabela Turma

CREATE TABLE Turma (
    
    ID_turma INT PRIMARY KEY,
    
    ID_curso INT,
    
    ID_professor INT,
    
    Horario_da_turma TIME,
    
    Dia_da_semana VARCHAR(20),
    
    Capacidade_maxima INT,
    
    Numero_de_alunos_matriculados INT,
    
    FOREIGN KEY (ID_curso) REFERENCES Curso(ID_curso),
    
    FOREIGN KEY (ID_professor) REFERENCES Professor(ID_professor)

);

-- Inserção de dados na tabela Aluno

INSERT INTO Aluno (ID_aluno, Nome, Endereco_rua, Endereco_cidade, Endereco_estado, Endereco_CEP, Email, Telefone_celular, Telefone_residencial, Data_de_matricula, Nivel_de_proficiencia)

VALUES

(1, 'João Silva', 'Rua A', 'Cidade A', 'Estado A', '12345-678', 'joao@email.com', '9999-9999', '8888-8888', '2022-01-15', 'Intermediário'),

(2, 'Maria Souza', 'Rua B', 'Cidade B', 'Estado B', '54321-876', 'maria@email.com', '7777-7777', '6666-6666', '2022-02-20', 'Avançado'),

(3, 'Luiza Oliveira', 'Rua C', 'Cidade C', 'Estado C', '98765-432', 'luiza@email.com', '1111-1111', '2222-2222', '2022-03-12', 'Básico'),

(4, 'Pedro Santos', 'Rua D', 'Cidade D', 'Estado D', '54321-000', 'pedro@email.com', '3333-3333', '4444-4444', '2022-04-18', 'Avançado'),

(5, 'Ana Carolina', 'Rua E', 'Cidade E', 'Estado E', '12345-678', 'ana.carol@email.com', '5555-5555', '6666-6666', '2022-05-25', 'Intermediário'),

(6, 'Marcos Fernandes', 'Rua F', 'Cidade F', 'Estado F', '13579-246', 'marcos@email.com', '7777-7777', '8888-8888', '2022-06-30', 'Avançado'),

(7, 'Julia Ribeiro', 'Rua G', 'Cidade G', 'Estado G', '98765-432', 'julia@email.com', '9999-9999', '1111-1111', '2022-07-10', 'Intermediário'),

(8, 'Rafaela Lima', 'Rua H', 'Cidade H', 'Estado H', '54321-000', 'rafaela@email.com', '2222-2222', '3333-3333', '2022-08-22', 'Básico'),

(9, 'Fernando Silva', 'Rua I', 'Cidade I', 'Estado I', '12345-678', 'fernando@email.com', '3333-3333', '5555-5555', '2022-09-05', 'Avançado'),

(10, 'Mariana Sousa', 'Rua J', 'Cidade J', 'Estado J', '13579-246', 'mariana@email.com', '4444-4444', '6666-6666', '2022-10-15', 'Intermediário'),

(11, 'Lucas Costa', 'Rua K', 'Cidade K', 'Estado K', '98765-432', 'lucas@email.com', '5555-5555', '7777-7777', '2022-11-20', 'Básico'),

(12, 'Camila Pereira', 'Rua L', 'Cidade L', 'Estado L', '54321-000', 'camila@email.com', '6666-6666', '8888-8888', '2022-12-28', 'Avançado'),

(13, 'Diego Rodrigues', 'Rua M', 'Cidade M', 'Estado M', '12345-678', 'diego@email.com', '7777-7777', '9999-9999', '2023-01-10', 'Intermediário'),

(14, 'Isabela Ferreira', 'Rua N', 'Cidade N', 'Estado N', '13579-246', 'isabela@email.com', '8888-8888', '1111-1111', '2023-02-14', 'Básico'),

(15, 'Gabriel Oliveira', 'Rua O', 'Cidade O', 'Estado O', '98765-432', 'gabriel@email.com', '9999-9999', '2222-2222', '2023-03-20', 'Avançado'),

(16, 'Amanda Santos', 'Rua P', 'Cidade P', 'Estado P', '54321-000', 'amanda@email.com', '1111-1111', '3333-3333', '2023-04-25', 'Intermediário'),

(17, 'Thiago Almeida', 'Rua Q', 'Cidade Q', 'Estado Q', '12345-678', 'thiago@email.com', '2222-2222', '4444-4444', '2023-05-30', 'Básico'),

(18, 'Laura Castro', 'Rua R', 'Cidade R', 'Estado R', '13579-246', 'laura@email.com', '3333-3333', '5555-5555', '2023-06-12', 'Avançado'),

(19, 'Felipe Martins', 'Rua S', 'Cidade S', 'Estado S', '98765-432', 'felipe@email.com', '4444-4444', '6666-6666', '2023-07-18', 'Intermediário'),

(20, 'Sophia Gomes', 'Rua T', 'Cidade T', 'Estado T', '54321-000', 'sophia@email.com', '5555-5555', '7777-7777', '2023-08-25', 'Básico');


-- Inserção de dados na tabela Professor

INSERT INTO Professor (ID_professor, Nome, Endereco_rua, Endereco_cidade, Endereco_estado, Endereco_CEP, Email, Telefone_celular, Telefone_residencial, Salario, Data_de_contratacao)

VALUES

(1, 'Carlos Oliveira', 'Rua X', 'Cidade Y', 'Estado Z', '98765-432', 'carlos@email.com', '5555-5555', '4444-4444', 3500.00, '2020-05-10'),

(2, 'Ana Pereira', 'Rua M', 'Cidade N', 'Estado O', '24680-135', 'ana@email.com', '3333-3333', '2222-2222', 3000.00, '2021-01-20'),

(3, 'Patricia Oliveira', 'Rua C', 'Cidade C', 'Estado C', '12345-678', 'patricia@email.com', '9999-9999', '8888-8888', 2800.00, '2021-01-15'),

(4, 'Ricardo Souza', 'Rua D', 'Cidade D', 'Estado D', '54321-876', 'ricardo@email.com', '7777-7777', '6666-6666', 3200.00, '2021-02-20'),

(5, 'Camila Silva', 'Rua E', 'Cidade E', 'Estado E', '98765-432', 'camila@email.com', '5555-5555', '4444-4444', 3000.00, '2021-03-25'),

(6, 'Fernando Pereira', 'Rua F', 'Cidade F', 'Estado F', '24680-135', 'fernando@email.com', '3333-3333', '2222-2222', 3500.00, '2021-04-30'),

(7, 'Mariana Santos', 'Rua G', 'Cidade G', 'Estado G', '12345-678', 'mariana@email.com', '1111-1111', '3333-3333', 3100.00, '2021-05-12'),

(8, 'Paulo Rodrigues', 'Rua H', 'Cidade H', 'Estado H', '54321-876', 'paulo@email.com', '2222-2222', '5555-5555', 2900.00, '2021-06-18'),

(9, 'Carla Almeida', 'Rua I', 'Cidade I', 'Estado I', '98765-432', 'carla@email.com', '3333-3333', '6666-6666', 3300.00, '2021-07-22'),

(10, 'Lucas Fernandes', 'Rua J', 'Cidade J', 'Estado J', '24680-135', 'lucas@email.com', '4444-4444', '7777-7777', 3000.00, '2021-08-30'),

(11, 'Vanessa Ribeiro', 'Rua K', 'Cidade K', 'Estado K', '12345-678', 'vanessa@email.com', '5555-5555', '8888-8888', 3200.00, '2021-09-05'),

(12, 'Gustavo Lima', 'Rua L', 'Cidade L', 'Estado L', '54321-876', 'gustavo@email.com', '6666-6666', '9999-9999', 3400.00, '2021-10-10'),

(13, 'Bruna Pereira', 'Rua M', 'Cidade M', 'Estado M', '98765-432', 'bruna@email.com', '7777-7777', '1111-1111', 3100.00, '2021-11-15'),

(14, 'Rodrigo Santos', 'Rua N', 'Cidade N', 'Estado N', '24680-135', 'rodrigo@email.com', '8888-8888', '2222-2222', 2800.00, '2021-12-20'),

(15, 'Aline Ferreira', 'Rua O', 'Cidade O', 'Estado O', '12345-678', 'aline@email.com', '9999-9999', '3333-3333', 3100.00, '2022-01-25'),

(16, 'Marcelo Oliveira', 'Rua P', 'Cidade P', 'Estado P', '54321-876', 'marcelo@email.com', '1111-1111', '4444-4444', 3200.00, '2022-02-28'),

(17, 'Tatiane Almeida', 'Rua Q', 'Cidade Q', 'Estado Q', '98765-432', 'tatiane@email.com', '2222-2222', '5555-5555', 3300.00, '2022-03-05'),

(18, 'Victor Silva', 'Rua R', 'Cidade R', 'Estado R', '24680-135', 'victor@email.com', '3333-3333', '6666-6666', 3000.00, '2022-04-10'),

(19, 'Luana Souza', 'Rua S', 'Cidade S', 'Estado S', '12345-678', 'luana@email.com', '4444-4444', '7777-7777', 2900.00, '2022-05-15'),

(20, 'Felipe Oliveira', 'Rua T', 'Cidade T', 'Estado T', '54321-876', 'felipe@email.com', '5555-5555', '8888-8888', 3100.00, '2022-06-20');


-- Inserção de dados na tabela Curso

INSERT INTO Curso (ID_curso, Nome_do_curso, Descricao_do_curso, Carga_horaria, Valor_do_curso, Tipo_de_curso)

VALUES

(1, 'Inglês Básico', 'Curso introdutório de inglês', 40, 500.00, 'Presencial'),

(2, 'Francês Intermediário', 'Curso intermediário de francês', 60, 800.00, 'Online'),

(3, 'Espanhol Avançado', 'Curso avançado de espanhol', 50, 750.00, 'Presencial'),

(4, 'Alemão Básico', 'Curso introdutório de alemão', 45, 700.00, 'Online'),

(5, 'Mandarim Intermediário', 'Curso intermediário de mandarim', 60, 900.00, 'Presencial'),

(6, 'Italiano Avançado', 'Curso avançado de italiano', 55, 800.00, 'Online'),

(7, 'Russo Básico', 'Curso introdutório de russo', 40, 600.00, 'Presencial'),

(8, 'Japonês Intermediário', 'Curso intermediário de japonês', 60, 850.00, 'Online'),

(9, 'Coreano Avançado', 'Curso avançado de coreano', 50, 780.00, 'Presencial'),

(10, 'Árabe Básico', 'Curso introdutório de árabe', 45, 720.00, 'Online'),

(11, 'Francês Avançado', 'Curso avançado de francês', 55, 850.00, 'Presencial'),

(12, 'Alemão Intermediário', 'Curso intermediário de alemão', 50, 780.00, 'Online'),

(13, 'Espanhol Básico', 'Curso introdutório de espanhol', 45, 700.00, 'Presencial'),

(14, 'Mandarim Avançado', 'Curso avançado de mandarim', 60, 900.00, 'Online'),

(15, 'Italiano Intermediário', 'Curso intermediário de italiano', 50, 780.00, 'Presencial'),

(16, 'Russo Avançado', 'Curso avançado de russo', 55, 820.00, 'Online'),

(17, 'Japonês Básico', 'Curso introdutório de japonês', 40, 650.00, 'Presencial'),

(18, 'Coreano Intermediário', 'Curso intermediário de coreano', 55, 800.00, 'Online'),

(19, 'Árabe Avançado', 'Curso avançado de árabe', 60, 880.00, 'Presencial'),

(20, 'Francês Intermediário', 'Curso intermediário de francês', 50, 760.00, 'Online');


-- Inserção de dados na tabela Matricula

INSERT INTO Matricula (ID_matricula, ID_aluno, ID_curso, Data_de_matricula, Status_de_pagamento, Valor_pago, Valor_pendente)

VALUES

(1, 1, 1, '2022-01-20', 'Pago', 400.00, 0),

(2, 2, 2, '2022-02-25', 'Pendente', 400.00, 400.00),

(3, 3, 3, '2022-03-20', 'Pago', 600.00, 0),

(4, 4, 4, '2022-04-25', 'Pendente', 550.00, 550.00),

(5, 5, 5, '2022-05-30', 'Pago', 800.00, 0),

(6, 6, 6, '2022-06-30', 'Pago', 720.00, 0),

(7, 7, 7, '2022-07-15', 'Pendente', 500.00, 500.00),

(8, 8, 8, '2022-08-22', 'Pago', 700.00, 0),

(9, 9, 9, '2022-09-28', 'Pendente', 650.00, 650.00),

(10, 10, 10, '2022-10-30', 'Pago', 780.00, 0),

(11, 11, 11, '2022-11-18', 'Pago', 800.00, 0),

(12, 12, 12, '2022-12-25', 'Pendente', 720.00, 720.00),

(13, 13, 13, '2023-01-30', 'Pago', 600.00, 0),

(14, 14, 14, '2023-02-28', 'Pendente', 780.00, 780.00),

(15, 15, 15, '2023-03-15', 'Pago', 750.00, 0),

(16, 16, 16, '2023-04-20', 'Pago', 670.00, 0),

(17, 17, 17, '2023-05-25', 'Pendente', 550.00, 550.00),

(18, 18, 18, '2023-06-30', 'Pago', 800.00, 0),

(19, 19, 19, '2023-07-18', 'Pago', 700.00, 0),

(20, 20, 20, '2023-08-25', 'Pendente', 760.00, 760.00);


-- Inserção de dados na tabela Turma

INSERT INTO Turma (ID_turma, ID_curso, ID_professor, Horario_da_turma, Dia_da_semana, Capacidade_maxima, Numero_de_alunos_matriculados)

VALUES

(1, 1, 1, '08:00', 'Segunda-feira', 25, 15),

(2, 2, 2, '18:00', 'Quarta-feira', 30, 20),

(3, 3, 3, '14:00', 'Segunda-feira', 30, 25),

(4, 4, 4, '09:00', 'Terça-feira', 25, 20),

(5, 5, 5, '18:30', 'Quarta-feira', 35, 30),

(6, 6, 6, '16:00', 'Quinta-feira', 30, 28),

(7, 7, 7, '20:00', 'Sexta-feira', 25, 20),

(8, 8, 8, '10:00', 'Segunda-feira', 20, 18),

(9, 9, 9, '15:30', 'Terça-feira', 30, 27),

(10, 10, 10, '13:00', 'Quarta-feira', 25, 22),

(11, 11, 11, '08:30', 'Quinta-feira', 35, 30),

(12, 12, 12, '14:00', 'Sexta-feira', 30, 27),

(13, 13, 13, '12:00', 'Segunda-feira', 25, 22),

(14, 14, 14, '19:30', 'Terça-feira', 30, 28),

(15, 15, 15, '10:30', 'Quarta-feira', 25, 20),

(16, 16, 16, '14:00', 'Quinta-feira', 35, 30),

(17, 17, 17, '12:00', 'Sexta-feira', 30, 25),

(18, 18, 18, '19:30', 'Segunda-feira', 25, 22),

(19, 19, 19, '10:30', 'Terça-feira', 30, 25),

(20, 20, 20, '14:00', 'Quarta-feira', 25, 20);

## CRUD

### Demonstração de Operações CRUD

Exemplos e prints demonstrando:
- Inserção de Dados.
- Leitura de Dados.
- Atualização de Dados.
- Exclusão de Dados.
![Modelagem de banco de dados completa - Sinomar-4_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/4e5b1712-a97c-4723-ac31-50ca7a9e4886)
![Modelagem de banco de dados completa - Sinomar-5_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/a4bc1e3a-be15-4825-a86a-d66b6874d8ff)
![Modelagem de banco de dados completa - Sinomar-6_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/faff0e8e-f837-4119-984b-47a12a3e4c28)
![Modelagem de banco de dados completa - Sinomar-7_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/f419036d-aad9-4e52-b5a2-d9550f159f15)
![Modelagem de banco de dados completa - Sinomar-8_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/7e04195e-e72c-48c5-8527-51d7aae81575)

## Relatórios

### Consultas SQL

1. Listar todos os alunos e seus respectivos cursos matriculados:
![Modelagem de banco de dados completa - Sinomar-9_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/399d97c4-e870-4fd5-94af-bb9fc112cbda)

2. Veja os cursos e seus professores relevantes:
![Modelagem de banco de dados completa - Sinomar-10_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/10ffe6e4-9b71-4992-9936-89aa5ca5d56a)

3. Exibir as matrículas dos alunos e seus respectivos status de pagamento:
![Modelagem de banco de dados completa - Sinomar-11_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/634ba44d-5be6-4e0e-8901-24ebb1a4f28c)

4. Listar todos os alunos matriculados em um curso específico:
![Modelagem de banco de dados completa - Sinomar-12_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/4ed2afe5-9406-4db5-a763-6ee8c4eabb40)

5. Exibir os professores e suas respectivas turmas:
![Modelagem de banco de dados completa - Sinomar-13_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/4f8f1cbc-9386-4cc3-9115-8c5797045899)

6. Mostrar os alunos ordenados por nível de proficiência:
![Modelagem de banco de dados completa - Sinomar-14_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/67699ef2-d95b-40b5-8c67-c55b2b832013)

7. Listar os cursos com carga horária acima de um valor específico:
![Modelagem de banco de dados completa - Sinomar-15_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/78a605d8-2ebc-4b32-8f17-0653c1daa1e6)

8. Exibir os alunos matriculados em mais de um curso:
![Modelagem de banco de dados completa - Sinomar-16_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/c55675b7-b440-4369-8cc2-091b700a9201)

9. Mostrar os alunos com nome iniciando pela letra 'A':
![Modelagem de banco de dados completa - Sinomar-17_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/89fa648a-fd63-4793-b497-8c2c8af45da2)

10. Listar as matrículas ordenadas por dados de matrícula:
![Modelagem de banco de dados completa - Sinomar-18_page-0001](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/assets/143889108/f58bc843-8171-43f4-96c1-7f780d987303)

    
## Código completo

[Código completo Sinomar.pdf](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/files/13454062/Codigo.completo.Sinomar.pdf)

## Complemento

[Modelagem de banco de dados completa - Sinomar.pdf](https://github.com/SinomarHenrique/Modelagem-de-banco-de-Dados/files/13454068/Modelagem.de.banco.de.dados.completa.-.Sinomar.pdf)
