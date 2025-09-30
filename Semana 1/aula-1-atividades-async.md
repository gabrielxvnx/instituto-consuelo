
# 🏡 Atividades Assíncronas

## 1. Pesquisa sobre SGBDs

**MySQL** é um SGBD relacional muito usado, principalmente em aplicações web (WordPress, Lojas Virtuais etc). É gratuito e de código aberto, mas também tem versão paga. Suporta SQL padrão, tem boa performance e funciona bem com PHP. É fácil de usar e instalar. A principal vantagem é a popularidade e comunidade forte. Como desvantagem, não tem tantos recursos avançados como o PostgreSQL, por exemplo.

Obs: Uma ferramenta muito usada junto com o MySQL é o HeidiSQL, que é um programa leve e gratuito para gerenciar bancos de dados via interface gráfica. Ele facilita a criação de tabelas, visualização de dados, execução de scripts SQL e exportações, sendo útil tanto para iniciantes quanto para quem já tem experiência.

---

## 2. Script SQL Prático

```sql
-- Criando tabela de categorias
CREATE TABLE categorias (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100)
);

-- Criando tabela de produtos com chave estrangeira para categorias
CREATE TABLE produtos (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100),
    preco DECIMAL(10,2),
    categoria_id INT REFERENCES categorias(id)
);

-- Inserindo categorias
INSERT INTO categorias (nome) VALUES
('Eletrônicos'),
('Roupas'),
('Livros'),
('Alimentos'),
('Móveis');

-- Inserindo produtos
INSERT INTO produtos (nome, preco, categoria_id) VALUES
('Notebook', 3500.00, 1),
('Camisa', 50.00, 2),
('Mesa de Jantar', 800.00, 5),
('Arroz', 20.00, 4),
('Livro SQL', 90.00, 3);

-- Consultas com WHERE
SELECT * FROM produtos WHERE preco > 100;
SELECT * FROM produtos WHERE preco < 100;
SELECT * FROM produtos WHERE categoria_id = 1;

-- Consulta com ORDER BY
SELECT * FROM produtos ORDER BY preco DESC;

```

---

## 3. Modelagem de Sistema

**Sistema escolhido:** Escola

**Tabelas:**

* alunos (id, nome, data_nascimento)
* cursos (id, nome, carga_horaria)
* matriculas (id, aluno_id, curso_id, data_matricula)

**Relacionamentos:**

* aluno pode estar em vários cursos → muitos pra muitos (resolvido com tabela de matrícula)
* curso pode ter vários alunos

**Tipos de dados:**

* `id` como SERIAL
* `nome` como VARCHAR
* `data` como DATE
* `carga_horaria` como INTEGER

**Chaves primárias e estrangeiras:**

* `alunos.id`, `cursos.id`, `matriculas.id` são primárias
* `matriculas.aluno_id` → FK para `alunos.id`
* `matriculas.curso_id` → FK para `cursos.id`

---

## 4. Leitura Complementar

Li a documentação do site W3 Schools conteúdo é simples e direto. Mostra a estrutura básica de comandos como SELECT, INSERT, UPDATE, DELETE, WHERE, JOIN, etc., com exemplos práticos. É bom pra quem está começando a praticar SQL e gosta de aprender testando online.

---

## 5. Reflexão Crítica

**SQL vs Excel**

SQL é bom pra quando você tem muitos dados, precisa de controle de integridade, relacionamentos e consultas mais complexas. Já Excel é bom pra análises rápidas, planilhas pequenas, ou pra quem não é da área de TI. Excel tem limite de linhas e não lida bem com múltiplas tabelas relacionadas. SQL é mais seguro, escalável e melhor pra sistemas reais. Excel é mais visual e prático pra tarefas manuais e pontuais.

---

## 6. Prática com Dataset Real

Usei um dataset de filmes do Kaggle em CSV.
<https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata>

**Passos:**

COPY movies FROM '/workspace/tmdb-movie-metadata/tmdb_5000_movies.csv' DELIMITER ',' CSV HEADER;

**Consultas:**

```sql
-- 1. Ver os 10 primeiros filmes
SELECT * FROM movies
LIMIT 10;

-- 2. Filmes lançados depois de 2010
SELECT original_title, release_year
FROM movies
WHERE release_year > 2010;

-- 3. Filmes com nota maior que 7
SELECT original_title, vote_average
FROM movies
WHERE vote_average > 7;

-- 4. Filmes ordenados por popularidade (top 10)
SELECT original_title, popularity
FROM movies
ORDER BY popularity DESC
LIMIT 10;

-- 5. Quantidade total de filmes no dataset
SELECT COUNT(*) AS total_filmes
FROM movies;

```

**Insights:**

* A maioria dos filmes com nota alta são antigos (antes de 2000)
* Depois de 2010, o número de filmes aumenta bastante.
* Os filmes mais populares nem sempre são os com melhor nota.

---
