# Gestão de Aluno, Disciplina e Professor

Este repositório contém pacotes desenvolvidos em PL/SQL para realizar operações relacionadas às entidades **Aluno**, **Disciplina** e **Professor** em um banco de dados Oracle.

## Estrutura do Projeto

### 1. PKG_ALUNO
Conjunto de procedures e cursores para gerenciar dados de alunos:
- **Procedure:** Exclusão de um aluno e todas as matrículas associadas.
- **Cursor:** Listagem de alunos com idade superior a 18 anos.
- **Cursor:** Listagem de alunos matriculados em um curso específico.

### 2. PKG_DISCIPLINA
Pacote para manipular dados de disciplinas:
- **Procedure:** Cadastro de uma nova disciplina, incluindo nome, descrição e carga horária.
- **Cursor:** Exibição de disciplinas com mais de 10 alunos matriculados.
- **Cursor:** Cálculo da média de idade dos alunos em uma disciplina específica.
- **Procedure:** Listagem de alunos matriculados em uma disciplina, com saída no console.

### 3. PKG_PROFESSOR
Ferramentas para gerenciar dados de professores:
- **Cursor:** Listagem de professores com mais de uma turma.
- **Function:** Cálculo do total de turmas em que um professor atua.
- **Function:** Retorno do nome do professor responsável por uma disciplina.

### 4. Como executar o código

 - Abra sua ferramenta de gerenciamento de banco de dados Oracle, como o SQL Developer.
 - Conecte-se ao banco de dados utilizando suas credenciais.
 - Copie o conteúdo do arquivo pacotes_entidades.sql.
 - Cole o conteúdo na área de consulta da ferramenta.
 - Execute o script para criar os pacotes e seus respectivos corpos.

## Estrutura Esperada do Banco de Dados

Antes de executar os pacotes, certifique-se de que as tabelas abaixo estão criadas no banco de dados:

- Tabela ALUNOS

CREATE TABLE ALUNOS (
    ID_ALUNO NUMBER PRIMARY KEY,
    NOME VARCHAR2(100),
    DATA_NASCIMENTO DATE,
    ID_CURSO NUMBER
);

- Tabela DISCIPLINAS

CREATE TABLE DISCIPLINAS (
    ID_DISCIPLINA NUMBER PRIMARY KEY,
    NOME VARCHAR2(100),
    DESCRICAO VARCHAR2(200),
    CARGA_HORARIA NUMBER
);

- Tabela PROFESSORES

CREATE TABLE PROFESSORES (
    ID_PROFESSOR NUMBER PRIMARY KEY,
    NOME VARCHAR2(100)
);

- Tabela MATRICULAS

CREATE TABLE MATRICULAS (
    ID_MATRICULA NUMBER PRIMARY KEY,
    ID_ALUNO NUMBER REFERENCES ALUNOS(ID_ALUNO),
    ID_DISCIPLINA NUMBER REFERENCES DISCIPLINAS(ID_DISCIPLINA),
    DATA_MATRICULA DATE
);

- Tabela TURMAS

CREATE TABLE TURMAS (
    ID_TURMA NUMBER PRIMARY KEY,
    ID_PROFESSOR NUMBER REFERENCES PROFESSORES(ID_PROFESSOR),
    ID_DISCIPLINA NUMBER REFERENCES DISCIPLINAS(ID_DISCIPLINA)
);
