# Processamento de Dados de Vendas

Este projeto fornece uma solução para processar e analisar um arquivo CSV de grande porte chamado vendas.csv, que contém dados de vendas de uma cadeia de varejo. O código é projetado para ser eficiente em termos de memória e capaz de lidar com grandes volumes de dados, mesmo em máquinas com memória limitada.

# Estrutura do Arquivo CSV

O arquivo vendas.csv contém as seguintes colunas:

Region: Região da venda
Country: País da venda
Item Type: Tipo de item vendido
Sales Channel: Canal de vendas
Order Priority: Prioridade do pedido
Order Date: Data do pedido
Order ID: ID do pedido
Ship Date: Data de envio
Units Sold: Unidades vendidas
Unit Price: Preço unitário
Unit Cost: Custo unitário
Total Revenue: Receita total
Total Cost: Custo total
Total Profit: Lucro total

# Objetivos

Leitura do Arquivo em Chunks: Ler o arquivo CSV de forma eficiente em partes menores para evitar problemas de memória.

Produto Mais Vendido: Identificar o produto mais vendido em termos de quantidade e canal.

Maior Volume de Vendas: Determinar qual país e região tiveram o maior volume de vendas em valor.

Média de Vendas Mensais: Calcular a média de vendas mensais por produto para o período disponível nos dados.

# Dependências

Pandas: Para manipulação de dados e leitura de arquivos CSV.

NumPy: Para operações numéricas (embora não seja explicitamente usado no código, pode ser necessário em algumas análises).

# Como Executar

Prepare o Ambiente: Certifique-se de que o arquivo vendas.csv está no mesmo diretório que o script Python ou forneça o caminho correto para o arquivo.

Execute o Script: Salve o código em um arquivo chamado processamento_vendas.py e execute-o usando Python.

Resultados: O script exibirá os seguintes resultados: O produto mais vendido em termos de quantidade e canal; O país e a região com o maior volume de vendas em valor; A média de vendas mensais por produto.

# Considerações

Ajuste do Tamanho do Chunk: O valor de chunk_size pode ser ajustado conforme a capacidade da memória da sua máquina.

Gerenciamento de Memória: O código utiliza o módulo gc para forçar a coleta de lixo e liberar memória após o processamento de cada chunk.
