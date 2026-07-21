# 🎸 Ecos Progressivos — End-to-End Marketing Performance Analytics

[Visitar o website Ecos Progressivos](https://ecosprogressivos.carrd.co/)

## Resumo do Projeto

O Ecos Progressivos é um projeto end-to-end de Marketing Analytics desenvolvido para analisar o desempenho de uma campanha digital de captação de subscritores para uma newsletter dedicada ao rock progressivo.

O projeto integra dados provenientes de Meta Ads, Google Analytics 4 e Mailchimp. Os dados foram tratados e consolidados em Python, preparados para armazenamento no SQL Server e utilizados na construção de um dashboard em Power BI.

O objetivo de negócio consistiu em analisar o funil de aquisição, identificar os principais pontos de perda e propor melhorias para aumentar a captação de subscritores.

## Competências Demonstradas

`Marketing Analytics` · `ETL` · `Python` · `pandas` · `SQL Server` · `Power BI` · `DAX` · `Google Analytics 4` · `Meta Ads` · `Mailchimp` · `Business Intelligence` · `Data Storytelling`

## Resultados Principais

- **Investimento Meta Ads:** 64,79 €
- **Impressões:** 25 386
- **Alcance:** 16 338 pessoas
- **Resultados atribuídos pela Meta:** 7
- **Sessões no website:** 532
- **Novos utilizadores:** 481
- **Inícios de formulário:** 43
- **Subscrições confirmadas:** 16
- **Taxa de início do formulário:** 8,08%
- **Taxa de conversão por sessão:** 3,01%
- **Rácio entre subscrições e inícios de formulário:** 37,21%
- **Custo por resultado atribuído pela Meta:** 9,26 €
- **Custo global por subscrição:** 4,05 €

## Stack Tecnológica e Arquitetura

- **Python e pandas:** importação, tratamento, transformação e consolidação dos relatórios CSV;
- **SQLAlchemy e pyodbc:** ligação entre Python e SQL Server;
- **SQL Server:** armazenamento da tabela analítica consolidada;
- **Power BI e DAX:** construção dos indicadores e visualização do funil;
- **Meta Ads:** dados de investimento e desempenho publicitário;
- **Google Analytics 4:** dados de tráfego e eventos do website;
- **Mailchimp:** validação das subscrições confirmadas.

## Pipeline de Dados

```text
Meta Ads ───────┐
                │
GA4 ────────────┼──> Python ETL ──> SQL Server ──> Power BI
                │
Mailchimp ──────┘
