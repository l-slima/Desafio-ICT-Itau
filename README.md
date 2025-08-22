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

📊 Resultados

Resumo Estatístico: A maioria das instâncias tem 4-64 vCPUs, 96 GiB de memória (máx. 32 TiB), e poucas possuem GPUs (máx. 8 com 1.4 TB de memória).
Modelo de Regressão: R² de 0.9303 e RMSE de 6.96, indicando alta precisão na previsão de custos.
Importância de Features: gpuCount é o principal fator de custo, seguido por vCpus e memorySizeInGiB, com storageTotalSizeInGB tendo impacto mínimo.
Gráficos: Disponíveis em images/ para comparação de previsões e análise de correlações.

🛠️ Tecnologias Utilizadas

Linguagem: Python
Bibliotecas: pandas, numpy, seaborn, matplotlib, scikit-learn
Ferramentas: Jupyter Notebook, Git

📝 Instruções de Uso

Clone o repositório: git clone <URL_DO_REPOSITORIO>.
Instale as dependências: pip install -r requirements.txt (crie um arquivo requirements.txt com as bibliotecas listadas).
Execute pipeline_analysis.ipynb para processar os dados e gerar o CSV tratado.
Execute ml_model.ipynb para treinar o modelo e visualizar os resultados.
Verifique os gráficos na pasta images/.

📌 Entregáveis

Código-fonte comentado: Disponível nos notebooks pipeline_analysis.ipynb e ml_model.ipynb.
Notebook: Explicações detalhadas e visualizações em ambos os notebooks.
Arquivo .csv: aws_pricing_tratado.csv com dados tratados.
Prints ou gráficos: Imagens geradas salvas em images/.

🤝 Contribuições
Contribuições são bem-vindas! Abra issues ou envie pull requests para sugerir melhorias, como adição de novos modelos (ex.: RandomForestRegressor) ou expansão do dataset.
📖 Licença
Este projeto é de uso interno do ICT Itaú. Para detalhes, consulte a equipe responsável.
