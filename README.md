# Tech Challenge – Fase 3 | Big Data & Analytics

## State of Data Brasil

Projeto desenvolvido para o Tech Challenge Fase 3, com foco na construção de uma solução de Engenharia de Dados e Analytics em ambiente AWS utilizando as pesquisas State of Data Brasil de 2023, 2024 e 2025.

O objetivo é organizar, tratar e analisar os dados para apoiar respostas sobre o mercado brasileiro de Dados, Analytics e Inteligência Artificial.

## Objetivos da análise

O projeto busca responder as seguintes questões:

- Como está estruturado o mercado brasileiro de Dados?
- Quais perfis profissionais são mais valorizados?
- Qual é o cenário de diversidade de gênero?
- Quais tecnologias possuem maior adoção?
- Qual é o índice de adoção de Inteligência Artificial e seu impacto?
- Existem diferenças por região, senioridade ou modelo de trabalho?
- Quais oportunidades e desafios existem para empresas que desejam investir em Dados e IA?

## Arquitetura

A solução utiliza uma arquitetura de Data Lake organizada nas camadas Bronze, Silver e Gold.

```text
State of Data
      ↓
AWS Glue
      ↓
Amazon S3 - Bronze
      ↓
AWS Glue + PySpark
      ↓
Amazon S3 - Silver
      ↓
AWS Glue + PySpark
      ↓
Amazon S3 - Gold
      ↓
AWS Glue Data Catalog
      ↓
Amazon Athena
      ↓
Power BI
```

![Arquitetura da solução](arquitetura/arquitetura_aws.jpeg)

## Tecnologias utilizadas

- AWS S3
- AWS Glue
- AWS Glue Data Catalog
- Apache Spark / PySpark
- Amazon Athena
- Jupyter / Glue Notebook
- Draw.io
- Power BI

## Camadas de dados

### Bronze

Contém os dados das três pesquisas em formato próximo ao original.

```text
workspace.tb_survey_2023
workspace.tb_survey_2024
workspace.tb_survey_2025
```

### Silver

Consolida e harmoniza os três anos em uma única tabela no nível de respondente.

```text
workspace.tb_state_of_data_silver
```

Principais tratamentos:

- harmonização de colunas entre os anos;
- tratamento de nulos;
- padronização de cargos, senioridade e modelo de trabalho;
- tratamento de campos multisseleção;
- criação de salário estimado;
- classificação de adoção de IA;
- deduplicação;
- particionamento por ano.

### Gold

Contém os dados agregados utilizados nas análises.

```text
workspace.tb_gold_mercado
workspace.tb_gold_diversidade
workspace.tb_gold_tecnologias
workspace.tb_gold_ia
workspace.tb_gold_segmentacoes
workspace.tb_gold_desafios
```

As tabelas Gold foram criadas para apoiar as análises de mercado, diversidade, tecnologias, IA, segmentações e desafios.

## Estrutura do repositório

```text
tech-challenge-fase-3/
│
├── README.md
├── notebooks/
│   ├── 01_raw_to_silver.py
│   ├── 02_silver_to_gold.py
│
│
├── arquitetura/
│   ├── arquitetura_aws.drawio
│   └── arquitetura_aws.png
│
│
└── presentation/
    └── tech_challenge_fase_3.pdf
```

## Fonte dos dados

State of Data Brasil — Data Hackers  
https://www.kaggle.com/datahackers/datasets

## Autores

```text
Armando Caliari Silva			      rm372117
Caike Herbe Jauch Soares			rm371123
Gabriel Santos de Oliveira Arruda		rm371178
Gustavo Ferreira da Silva Santana		rm370545
Kauan Lucas Gomes Jardim			rm370438
```


