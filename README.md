# 🎸 Ecos Progressivos: End-to-End Marketing Performance Analytics

## Resumo do Projeto
Este projeto demonstra a criação de um pipeline completo de dados (ETL, Armazenamento e Business Intelligence) para analisar o funil de conversão de uma campanha de marketing digital. O objetivo de negócio foi otimizar a captação de subscritores para uma newsletter de nicho (Rock Progressivo), integrando dados de três plataformas distintas.

Skills Demonstrated
 Marketing Analytics
 ETL
 Python
 SQL
 Power BI
 Google Analytics 4
 Meta Ads
 Business Intelligence
 Data Storytelling

**Resultados Principais:**
* **Investimento:** 64,79 €
* **Taxa de Conversão da Página:** 3.3% (16 Subscrições Finais / 481 Visitas)
* **Custo Por Aquisição (CPA):** 4,06 €

## Tech Stack & Arquitetura
* **Python (pandas, sqlalchemy, pyodbc):** Extração, tratamento e transformação (ETL) dos relatórios em bruto (CSV).
* **SQL Server (Localhost):** Armazenamento relacional e estruturação do modelo de dados.
* **Power BI & DAX:** Visualização de dados, modelação semântica e UI/UX (Dark Mode temático).
* **Fontes de Dados:** Meta Ads (Facebook/Instagram), Google Analytics 4 (GA4), Mailchimp.

## Engenharia de Dados: A Decisão Arquitetónica
O maior desafio técnico foi unificar dados de plataformas com naturezas completamente diferentes (impressões de anúncios vs. eventos de web analytics vs. registos de e-mail). 

**Solução:** Em vez de construir uma tabela horizontal, o script Python foi desenvolvido para transformar os dados num formato vertical/Long Format (data_registo | plataforma | metrica| valor). 
Isto garante **escalabilidade total**: o repositório está preparado para receber novas plataformas de marketing no futuro sem necessidade de restruturar as tabelas SQL.

## Business Intelligence & Design Analítico
O dashboard em Power BI foi desenhado com foco na experiência do utilizador e na clareza acionável, evitando o comum "ruído visual":
* **O Problema do "Efeito Penhasco":** Inicialmente, colocar 25.386 impressões no mesmo funil de 16 subscrições esmagava a visualização.
* **A Solução:** Separação do tráfego de topo de funil (Meta Ads) em cartões de KPI de leitura rápida, dedicando o gráfico de funil exclusivamente à jornada dentro da Landing Page:
*   Visitas (481) Inicio Formulario (43) Subscrições (16)


adicionar foto dashboard

## Insights e Próximos Passos (Recomendação Estratégica)
A análise detalhada do funil revelou um estrangulamento claro: embora 43 utilizadores tenham demonstrado intenção ao iniciar o formulário, apenas 16 o concluíram. 

**Plano de Ação Proposto:**
1. **Otimização de Fricção (CRO):** Reduzir os campos do formulário no Carrd.co ou implementar um sistema de subscrição em 1-clique para diminuir a taxa de abandono do formulário.
2. **Ativação de Google Ads (Tráfego de Intenção vs. Interrupção):** A campanha Meta baseou-se em interrupção de *scroll*. O próximo passo estratégico é alocar orçamento para a Rede de Pesquisa do Google Ads (ex: *"newsletter vinil rock"*). A hipótese a testar é que o tráfego de pesquisa intencional terá uma taxa de conversão no formulário significativamente superior aos atuais 37% (16/43), baixando potencialmente o CPA global.
