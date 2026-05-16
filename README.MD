# Clusterização de Exames Laboratoriais

## Descrição do Projeto

Este projeto tem como objetivo estruturar e analisar dados laboratoriais originalmente não padronizados, aplicando técnicas de pré-processamento e clusterização para identificar padrões na solicitação de exames.

Os dados apresentavam alto nível de ruído, inconsistências e formato inadequado para análise, exigindo a construção de um pipeline completo de tratamento antes da aplicação de modelos de Machine Learning.

---

## Objetivo

Aplicar técnicas de aprendizado não supervisionado, utilizando o algoritmo K-Means Clustering, com os seguintes objetivos:

* Identificar padrões na solicitação de exames laboratoriais
* Agrupar registros com características semelhantes
* Reduzir a complexidade de um dataset de alta dimensionalidade
* Extrair insights sobre comportamento operacional e clínico

---

## Dataset

O dataset é composto por registros laboratoriais com as seguintes características:

* Dados originalmente não estruturados
* Todas as colunas no formato `string`
* Exames registrados como múltiplos valores em uma única célula
* Presença de dados sensíveis (ex: nome e usuário)

---

## Tratamento de Dados Sensíveis

Foram removidas colunas contendo informações pessoais, garantindo anonimização e conformidade com boas práticas de privacidade:

* Nome
* Usuário

---

## Pré-processamento

Para viabilizar a análise, foi necessário estruturar completamente o dataset:

* Separação dos exames contidos em uma única célula
* Padronização dos nomes dos exames
* Remoção de inconsistências e ruídos
* Conversão dos dados para formato estruturado

---

## Engenharia de Features

Após o tratamento:

* Aplicação de **One-Hot Encoding** para representar os exames
* Criação de aproximadamente **71 variáveis binárias**
* Cada linha passou a representar a presença (1) ou ausência (0) de um exame

---

## Preparação para Modelagem

Antes da clusterização:

* Padronização dos dados utilizando **StandardScaler**
* Garantia de que todas as variáveis contribuam de forma equilibrada no cálculo de distância

---

## Modelagem

Foi aplicado o algoritmo **K-Means Clustering** para segmentação dos dados.

### Definição do número de clusters

Foram utilizados:

* Método do cotovelo (Elbow Method)
* Silhouette Score
* Análise visual com PCA

Apesar de pequenas variações métricas, a análise indicou que:

> **Os dados apresentam duas estruturas principais, sendo mais adequado o uso de k = 2 para melhor interpretabilidade.**

---

##  Análise dos Clusters

A análise revelou dois grupos distintos com comportamentos bem definidos.

### Cluster 1 — Baixa complexidade (≈77%)

* Maioria dos registros
* Média de aproximadamente **4,6 exames por paciente**
* Solicitações pontuais e menos diversificadas

Interpretação:
Perfil associado a atendimentos de rotina, triagem ou baixa complexidade.

---

### Cluster 0 — Alta complexidade (≈23%)

* Menor proporção de registros
* Média de aproximadamente **18 exames por paciente**
* Maior diversidade e combinação de exames

Interpretação:
Perfil associado a investigação clínica mais aprofundada ou acompanhamento ambulatorial.

---
### Dashboard

---

## Insights

A análise permite extrair um padrão relevante:

> **Embora represente uma menor proporção dos atendimentos, o cluster de maior complexidade concentra maior volume total de exames e apresenta, em média, quase quatro vezes mais exames por paciente.**

Esse comportamento indica:

* Concentração de consumo de recursos laboratoriais
* Diferença clara entre perfis de atendimento
* Existência de padrões não aleatórios na solicitação de exames

---

## Conclusão

A aplicação de técnicas de clusterização permitiu identificar padrões estruturais relevantes em dados originalmente desorganizados.

Os resultados mostram que:

* As solicitações laboratoriais seguem perfis distintos
* Existe uma separação clara entre baixa e alta complexidade
* Uma parcela menor dos registros é responsável por maior carga operacional

Esse tipo de análise pode apoiar:

* Planejamento de recursos laboratoriais
* Otimização de fluxos de atendimento
* Melhor compreensão do comportamento clínico e operacional

---

## Próximos Passos

* Análise de associação entre exames (Apriori / FP-Growth)
* Desenvolvimento de dashboard para visualização dos padrões
* Exploração de outros algoritmos de clusterização (DBSCAN, Hierárquico)

Isac Renan Miranda de Oliveira
