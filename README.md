# Análise Preditiva de Evasão de Clientes (Churn) - TelecomX

## Visão Geral do Projeto

Este projeto tem como objetivo principal identificar os fatores que levam os clientes da TelecomX a cancelar seus serviços (churn) e desenvolver modelos de Machine Learning capazes de **prever** essa evasão. Através da análise e modelagem, busca-se fornecer insights acionáveis para que a empresa possa implementar estratégias de retenção de clientes mais eficazes e proativas. A retenção de clientes é um pilar fundamental para a saúde financeira de qualquer negócio de serviços, e a compreensão e previsão do churn são passos cruciais para garantir a lealdade do cliente.

O projeto foi desenvolvido em Python, utilizando bibliotecas populares de manipulação de dados, visualização e Machine Learning.

## Estrutura do Projeto

O core do projeto está contido no notebook Jupyter `TelecomX_analise_preditiva.ipynb`, que segue as seguintes etapas:

1.  **Extração de Dados**: Carregamento dos dados de uma API (ou arquivo local, se a API estiver indisponível).
2.  **Transformação e Limpeza dos Dados**:
    * Expansão de colunas aninhadas (dicionários e listas).
    * Tratamento de valores ausentes e duplicados.
    * Conversão de tipos de dados.
    * Criação de novas features (ex: `Contas_Diarias`).
    * Padronização de variáveis categóricas binárias (Yes/No para 1/0).
3.  **Preparação dos Dados para Modelagem**:
    * Remoção de colunas irrelevantes (`customerID`).
    * Encoding de variáveis categóricas remanescentes via One-Hot Encoding.
    * Verificação da proporção da variável alvo (`Churn`) para identificar desbalanceamento de classes.
    * Normalização/Padronização de features numéricas (usando `StandardScaler`).
4.  **Modelagem Preditiva**:
    * Divisão dos dados em conjuntos de treino e teste (70/30) com estratificação.
    * Treinamento e avaliação de dois modelos de classificação:
        * **Regressão Logística**: Modelo linear, interpretável, requer dados escalados.
        * **Random Forest**: Modelo de ensemble robusto, não sensível à escala dos dados.
    * Avaliação dos modelos utilizando métricas como Acurácia, Precisão, Recall, F1-score e Matriz de Confusão.
5.  **Análise de Importância das Variáveis**: Identificação das features mais influentes para cada modelo, fornecendo insights sobre os principais impulsionadores do churn.
6.  **Relatório Final**: Um relatório textual detalhado das conclusões, comparações entre os modelos e recomendações estratégicas baseadas nos insights obtidos.

## Tecnologias Utilizadas

* **Python**
* **Bibliotecas Python**:
    * `pandas`: Manipulação e análise de dados.
    * `numpy`: Operações numéricas.
    * `matplotlib` e `seaborn`: Visualização de dados.
    * `requests` e `json`: Interação com APIs.
    * `scipy`: Funções científicas e estatísticas.
    * `sklearn` (scikit-learn): Ferramentas de Machine Learning (pré-processamento, modelos, métricas).
    * `imblearn` (imbalanced-learn): (Opcional, comentado no notebook) Para balanceamento de classes como SMOTE.

## Como Executar o Projeto

Para replicar a análise e os modelos:

1.  **Clone o Repositório**:
    ```bash
    git clone [https://github.com/ingridcristh/challenge2-data-science.git](https://github.com/ingridcristh/challenge2-data-science.git)
    cd challenge2-data-science
    ```

2.  **Crie e Ative um Ambiente Virtual (Recomendado)**:
    ```bash
    python -m venv venv
    # No Windows:
    .\venv\Scripts\activate
    # No macOS/Linux:
    source venv/bin/activate
    ```

3.  **Instale as Dependências**:
    ```bash
    pip install pandas numpy matplotlib seaborn requests scikit-learn
    # Se for usar o balanceamento de classes (descomentar no notebook):
    # pip install imbalanced-learn
    ```

4.  **Execute o Notebook Jupyter**:
    ```bash
    jupyter notebook TelecomX_analise_preditiva.ipynb
    ```
    Isso abrirá o Jupyter Notebook no seu navegador. Você pode então executar as células sequencialmente para ver todas as etapas da análise, limpeza, modelagem e geração do relatório.

## Fonte dos Dados

Os dados são obtidos de uma API pública (ou um arquivo JSON no GitHub), simulando um dataset de clientes de telecomunicações.

* **URL da API**: `https://raw.githubusercontent.com/ingridcristh/challenge2-data-science/main/TelecomX_Data.json`

## Análise e Resultados Principais

O relatório final, gerado dentro do próprio notebook, detalha as conclusões, mas os pontos-chave incluem:

* **Fatores Chave de Churn**: `customer_tenure` (tempo de contrato), `account_Contract_Month-to-month` (contrato mensal), `internet_InternetService_Fiber optic` (serviço de fibra óptica), `account_Charges_Monthly` (faturamento mensal) e `account_PaymentMethod_Electronic check` (método de pagamento por cheque eletrônico) foram identificados como os preditores mais significativos de evasão.
* **Desempenho dos Modelos**: O **Random Forest** demonstrou ser o modelo de melhor desempenho em termos de acurácia, precisão, recall e F1-score para este dataset, superando a Regressão Logística.
* **Desbalanceamento de Classes**: A variável alvo `Churn` apresenta desbalanceamento (mais clientes "Não Churn" do que "Churn"), o que pode impactar o desempenho de modelos na classe minoritária. O balanceamento de classes é uma melhoria recomendada para futuras iterações.

## Recomendações Estratégicas

Com base na análise, foram propostas as seguintes estratégias de retenção:

1.  **Foco nos Primeiros Meses**: Programas de onboarding robustos e proativos para novos clientes.
2.  **Incentivos a Contratos Longos**: Oferecer benefícios para clientes que optam por contratos anuais ou bianuais.
3.  **Otimização da Experiência da Fibra Óptica**: Investigar e melhorar a satisfação de clientes de fibra óptica.
4.  **Gestão de Valor**: Oferecer soluções personalizadas para clientes com faturamento mensal alto.
5.  **Melhoria da Experiência de Pagamento**: Otimizar o processo de pagamento e incentivar métodos mais convenientes.
6.  **Sistema de Alerta de Churn**: Implementar o modelo preditivo para identificar proativamente clientes de alto risco.

