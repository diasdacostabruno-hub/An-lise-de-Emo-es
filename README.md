# 🧠 Sentiment AI Analyzer

Aplicação web desenvolvida com **Python**, **Streamlit**, **SpaCy** e **PostgreSQL Neon**, criada para coletar feedbacks de usuários, analisar o sentimento do texto informado e salvar os dados em um banco de dados.

---

## 📌 Descrição do Projeto

O **Sentiment AI Analyzer** permite que o usuário preencha um formulário com:

* Nome completo
* CPF
* Feedback/opinião

Após o envio, a aplicação realiza uma análise simples de sentimento utilizando processamento de linguagem natural com **SpaCy** e classifica o comentário como:

* 🟢 Positivo
* 🔴 Negativo

Os dados são salvos automaticamente em uma tabela PostgreSQL hospedada no **Neon Tech**.

---

## 🧩 Categorias do Projeto

* Inteligência Artificial
* Processamento de Linguagem Natural
* Análise de Sentimentos
* Aplicação Web
* Banco de Dados
* Python
* Streamlit

---

## 🚀 Funcionalidades

* Interface web moderna com Streamlit
* Formulário para coleta de feedback
* Análise de sentimento em português
* Conexão com banco PostgreSQL Neon
* Criação automática da tabela no banco de dados
* Salvamento dos dados enviados
* Exibição das últimas análises realizadas
* Feedback visual com mensagens de sucesso, alerta e animações

---

## 🛠️ Tecnologias Utilizadas

* Python
* Streamlit
* SpaCy
* PostgreSQL
* Neon Database
* Psycopg2

---

## 📚 Bibliotecas Utilizadas

```python
import os
import psycopg2
import spacy
import streamlit as st
```

---

## 🧠 Como funciona a análise de sentimento

A análise é feita por meio de uma heurística simples baseada em palavras-chave.

O sistema verifica se o texto contém palavras positivas ou negativas.

### Palavras positivas usadas no projeto

* bom
* boa
* ótimo
* excelente
* gostei
* amei
* feliz
* top
* legal
* maravilhoso

### Palavras negativas usadas no projeto

* ruim
* péssimo
* odiei
* horrível
* triste
* chato
* difícil
* mal

Se a pontuação final for maior ou igual a zero, o sentimento é classificado como **Positivo**.
Caso contrário, o sentimento é classificado como **Negativo**.

---

## 🗄️ Estrutura da Tabela no Banco de Dados

A aplicação cria automaticamente a tabela `avaliacoes_sentimento`, caso ela ainda não exista.

```sql
CREATE TABLE IF NOT EXISTS avaliacoes_sentimento (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    cpf VARCHAR(14) NOT NULL,
    texto_sentimento TEXT NOT NULL,
    resultado_analise VARCHAR(10) NOT NULL
);
```

---

## ⚙️ Variáveis de Ambiente

Para conectar o projeto ao banco Neon, é necessário configurar a variável de ambiente:

```env
DATABASE_URL=sua_url_de_conexao_do_neon
```

Exemplo:

```env
DATABASE_URL=postgresql://usuario:senha@host/database?sslmode=require
```

---

## ▶️ Como executar o projeto localmente

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
```

### 2. Acesse a pasta do projeto

```bash
cd seu-repositorio
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

### 4. Baixe o modelo SpaCy em português

```bash
python -m spacy download pt_core_news_sm
```

### 5. Configure a variável de ambiente

No terminal, adicione sua URL do Neon:

```bash
export DATABASE_URL="sua_url_do_neon"
```

No Windows PowerShell:

```bash
$env:DATABASE_URL="sua_url_do_neon"
```

### 6. Execute o projeto

```bash
streamlit run app.py
```

---

## 🌐 Deploy

Este projeto pode ser publicado em plataformas como:

* Render
* Streamlit Community Cloud
* Railway
* Heroku

Para deploy, configure a variável de ambiente `DATABASE_URL` na plataforma escolhida.

---

## 📄 Arquivo requirements.txt

```txt
streamlit
spacy
psycopg2-binary
```

---

## 📄 Arquivo runtime.txt

```txt
python-3.11.9
```

---

## 📌 Observações importantes

* O projeto utiliza uma análise de sentimento simples baseada em palavras-chave.
* Para uso em produção, é recomendado utilizar um modelo treinado de NLP ou uma biblioteca específica para análise de sentimentos em português.
* O CPF é armazenado no banco de dados, então é importante aplicar boas práticas de segurança e privacidade.
* A variável `DATABASE_URL` não deve ser exposta publicamente no GitHub.

---

## 👩‍💻 Autora

Projeto desenvolvido por Nátaly Antunes Madeira.

---

## 📜 Licença

Este projeto é de uso educacional e pode ser adaptado conforme a necessidade.
