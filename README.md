Projeto: Trilha A – Dados & IA - Análise de Custos de Nuvem AWS
📋 Descrição
Este projeto, desenvolvido como parte da Trilha A – Dados & IA do ICT Itaú, cria um pipeline de ingestão e processamento de dados em Python a partir de dados públicos de custos de instâncias AWS. Inclui um modelo de machine learning (regressão linear) para prever custos (preço on-demand Linux por hora) e análise exploratória para identificar padrões de uso. O objetivo é suportar decisões estratégicas relacionadas a custos de nuvem.

👤 Autor

Nome: Lucas de Souza Lima 

🎯 Objetivos

Desenvolver um pipeline para ingerir, tratar e analisar dados de preços de instâncias AWS.
Aplicar regressão linear para prever custos com base em recursos como vCPUs, memória, armazenamento e GPUs.
Realizar análise exploratória com visualizações e estatísticas descritivas.
Gerar entregáveis conforme especificado (código comentado, notebook, CSV tratado, gráficos).

📂 Estrutura do Projeto

Pipeline_Lucas_Lima.ipynb: Notebook Jupyter com o pipeline de ingestão, tratamento de dados, análise exploratória e visualizações.
regressão.ipynb: Notebook com o modelo de machine learning (regressão linear) e avaliação.
aws_pricing_tratado.csv: Arquivo CSV contendo os dados tratados após processamento.
images/: Diretório com gráficos gerados (ex.: Previsão vs Real, Importância das Features).
README.md: Este arquivo com documentação do projeto.

🚀 Funcionalidades

Ingestão e Tratamento: Carrega e trata dados ausentes do dataset AWS, salvando em aws_pricing_tratado.csv.
Análise Exploratória: Gera resumos estatísticos e visualizações (histogramas, correlações) para recursos como vCPUs, memória e GPUs.
Modelo de Machine Learning: Usa regressão linear para prever o preço on-demand Linux por hora, avaliado por R² e RMSE.
Visualizações: Inclui gráficos de previsão vs real e importância de features.

## 📊 Resultados
### Análise Exploratória
- **Distribuição de Recursos:**
  - **vCPUs:** Concentração em valores baixos (0-100), com uma cauda longa até 800 vCPUs, indicando instâncias de alta performance para HPC e big data.
  - **Memória (memorySizeInGiB):** Maioria com até 5000 GiB, mas com extremos até 32 TiB, otimizadas para bancos de dados in-memory ou machine learning.
  - **GPUs (gpuCount):** Predominância de 0 GPUs, com raros casos de até 8 GPUs, voltados para Deep Learning e renderização.
  - **Memória Total de GPU (gpuTotalGpuMemoryInGiB):** Quase todas as instâncias têm 0 GiB, mas algumas alcançam 1400 GiB, ideais para modelos de IA grandes.
  - **Interfaces de Rede (maxNetworkInterfaces):** Picos em 2-15 ENIs, com até 80 em instâncias de alta escalabilidade.
- **Resumo Estatístico:**
  - **vCPUs:** Média de 41.8, mediana de 16, máximo de 896.
  - **Memória:** Média de 272.8 GiB, mediana de 96 GiB, máximo de 32 TiB.
  - **Armazenamento:** Média de 2469.4 GB, mediana de 0 GB, máximo de 335 TB.
  - **GPUs:** Média de 0.12, mediana de 0, máximo de 8.
  - **ENIs:** Média de 8.3, mediana de 8, máximo de 80.
- **Insights Iniciais:** A maioria das instâncias é básica (baixa CPU, memória moderada, sem GPU), mas há opções especializadas para computação intensa, IA e rede escalável.

### Correlação com Preço On-Demand Linux
- **vCPUs x Preço:** Correlação forte (0.77), destacando vCPUs como driver de custo.
- **Memória RAM x Preço:** Correlação muito forte (0.94), sendo o fator mais determinante.
- **Armazenamento x Preço:** Correlação fraca (0.14), indicando custo separado (via EBS).
- **GPUs x Preço:** Correlação fraca (0.23), com impacto dependendo da família da instância.
- **Conclusão da Correlação:** O preço é dominado por CPU e memória, enquanto armazenamento e GPUs têm influência secundária.

### Modelo de Machine Learning
- **Regressão Linear:**
  - **Target:** Preço on-demand Linux por hora (`onDemandLinuxHr`).
  - **Features:** `vCpus`, `memorySizeInGiB`, `storageTotalSizeInGB`, `gpuCount`.
  - **Desempenho:**
    - **R²:** 0.9303 (93% da variabilidade do preço explicada).
    - **RMSE:** 6.96 (erro médio baixo em relação à escala dos preços).
  - **Coeficientes:**
    - `gpuCount`: 1.765 (maior impacto).
    - `vCpus`: 0.0242.
    - `memorySizeInGiB`: 0.0092.
    - `storageTotalSizeInGB`: 0.000039 (mínimo impacto).
- **Visualizações:**
  - **Previsão vs Real:** Gráfico mostra proximidade entre valores previstos e reais, com linha de perfeição indicando boa acurácia.
  - **Importância das Features:** `gpuCount` destaca-se como principal fator, seguido por `vCpus` e `memorySizeInGiB`, corroborando a análise de correlação.

### Conclusão Geral dos Resultados
O pipeline demonstrou que:
- A maioria das instâncias AWS atende workloads básicas, mas há nichos para alta performance (HPC, IA, rede intensiva).
- A regressão linear prevê custos com alta precisão (R² de 0.93), validando CPU, memória e GPUs como drivers principais.
- Armazenamento tem impacto negligenciável no preço on-demand, alinhado com a política de tarifação da AWS.
- Os gráficos e o CSV tratado (`aws_pricing_tratado.csv`) fornecem uma base sólida para decisões estratégicas no ICT Itaú.

🛠️ Tecnologias Utilizadas

Linguagem: Python
Bibliotecas: pandas, numpy, seaborn, matplotlib, scikit-learn
Ferramentas: Jupyter Notebook, Git
