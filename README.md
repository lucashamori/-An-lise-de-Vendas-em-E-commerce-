# -Análise-de-Vendas-em-E-commerce-
"Análise de Tendências de Vendas em E-commerce: Como Categoria e Pagamento Impactam a Receita" Estudo realizado para aprendizado de análise de dados.


1. Importação de Bibliotecas
python
Copiar código
import pandas as pd
import matplotlib.pyplot as plt
Explicação:

Pandas é utilizado para manipulação e análise de dados.
Matplotlib é utilizado para criar gráficos e visualizações dos resultados.
2. Carregar o Dataset
python
Copiar código
data = pd.read_csv('ecommerce_dataset_updated.csv')
Explicação:

A função pd.read_csv é utilizada para carregar o dataset no formato CSV para um DataFrame do Pandas. Essa etapa é importante para começarmos a trabalhar com os dados.
3. Visualizar as Primeiras Linhas do Dataset
python
Copiar código
data.head()
Explicação:

data.head() exibe as primeiras 5 linhas do dataset. Isso ajuda a dar uma olhada inicial nas informações contidas e entender a estrutura do dataset.
4. Informações Gerais do Dataset
python
Copiar código
data.info()
Explicação:

data.info() exibe informações sobre as colunas do dataset, como o tipo de dado e a quantidade de valores não nulos. Isso é útil para verificar se há colunas com valores ausentes.
5. Limpeza de Dados
5.1. Verificar Valores Ausentes
python
Copiar código
data.isnull().sum()
Explicação:

isnull() verifica se há valores ausentes no dataset. A função sum() retorna o total de valores ausentes por coluna.
5.2. Remover Valores Duplicados
python
Copiar código
data = data.drop_duplicates()
Explicação:

drop_duplicates() remove qualquer linha duplicada do DataFrame, garantindo que os dados usados nas análises sejam únicos.
5.3. Remover Espaços em Branco nos Nomes das Colunas
python
Copiar código
data.columns = data.columns.str.strip()
Explicação:

Remove os espaços extras no início ou no final dos nomes das colunas. Isso é importante para evitar problemas ao acessar as colunas do DataFrame.
6. Conversão de Formatos de Data
python
Copiar código
data['Purchase_Date'] = pd.to_datetime(data['Purchase_Date'], format='%d-%m-%Y')
Explicação:

pd.to_datetime() converte a coluna Purchase_Date para o formato datetime para que possamos manipulá-la de forma mais eficiente. O parâmetro format='%d-%m-%Y' especifica o formato da data no dataset.
7. Análise Exploratória de Dados (EDA)
7.1. Análise de Receita por Categoria
python
Copiar código
categoria_receita = data.groupby('Category')['Final_Price(Rs.)'].sum().sort_values(ascending=False)
Explicação:

groupby('Category') agrupa os dados pela categoria.
['Final_Price(Rs.)'].sum() soma a receita para cada categoria.
sort_values(ascending=False) ordena as categorias pela receita, da maior para a menor.
7.2. Visualização de Receita por Categoria
python
Copiar código
categoria_receita.plot(kind='bar', color='skyblue', edgecolor='black', figsize=(10,6))
plt.title('Receita por Categoria', fontsize=16)
plt.xlabel('Categoria', fontsize=12)
plt.ylabel('Receita Total (Rs.)', fontsize=12)
plt.xticks(rotation=45)
plt.show()
Explicação:

O gráfico de barras permite visualizar de forma clara qual categoria gerou mais receita.
8. Análise de Receita por Método de Pagamento
python
Copiar código
metodos_pagamento_receita = data.groupby('Payment_Method')['Final_Price(Rs.)'].sum().sort_values(ascending=False)
Explicação:

Aqui, estamos agrupando os dados pelo método de pagamento e somando a receita para cada método.
8.1. Visualização de Receita por Método de Pagamento
python
Copiar código
metodos_pagamento_receita.plot(kind='bar', color='lightgreen', edgecolor='black', figsize=(10, 6))
plt.title('Receita por Método de Pagamento', fontsize=16)
plt.xlabel('Método de Pagamento', fontsize=12)
plt.ylabel('Receita Total (Rs.)', fontsize=12)
plt.xticks(rotation=45)
plt.show()
Explicação:

O gráfico de barras mostra quais métodos de pagamento são mais utilizados e qual geraram mais receita.
9. Receita Mensal
python
Copiar código
data['Year-Month'] = data['Purchase_Date'].dt.to_period('M')
receita_mensal = data.groupby('Year-Month')['Final_Price(Rs.)'].sum()
Explicação:

Criamos uma coluna Year-Month para agrupar os dados por mês e calcular a receita mensal.
9.1. Visualização de Receita Mensal
python
Copiar código
plt.figure(figsize=(12, 6))
receita_mensal.plot(kind='line', color='skyblue', marker='o', linestyle='-', linewidth=2)
plt.title('Receita Mensal', fontsize=16)
plt.xlabel('Ano-Mês', fontsize=12)
plt.ylabel('Receita Total (Rs.)', fontsize=12)
plt.xticks(rotation=45)
plt.grid(True)
plt.show()
Explicação:

O gráfico de linha mostra como a receita varia ao longo dos meses, ajudando a identificar padrões sazonais.
Conclusão
Com esse projeto, eu aprendi a realizar a limpeza de dados, aplicar técnicas de análise exploratória, gerar visualizações e realizar a conversão de tipos de dados de forma eficaz. 
