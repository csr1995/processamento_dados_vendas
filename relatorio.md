# Relatório: Solução para Processamento de Grandes Volumes de Dados

# Introdução

Este relatório descreve a abordagem adotada para processar e analisar um arquivo CSV de grande porte, denominado vendas.csv, com aproximadamente 5GB. O objetivo é abordar o problema de grandes volumes de dados de forma eficiente, garantindo que a solução possa ser executada em máquinas com memória limitada. O código foi projetado para realizar a leitura e análise de dados em partes menores, utilizando técnicas de otimização de memória e processamento.

# Abordagem e Estratégias Implementadas

1. Leitura em Chunks

    Problema: Carregar um arquivo de 5GB inteiro na memória pode causar problemas de falta de memória (Out of Memory) e degradação de desempenho.

    Solução: Para mitigar este problema, a leitura do arquivo é realizada em partes menores, ou "chunks", utilizando o parâmetro chunksize da função pd.read_csv da biblioteca Pandas. Cada chunk contém um número específico de linhas (definido como 50.000 linhas no exemplo). Esta abordagem permite que o processamento de dados seja feito em pedaços menores, reduzindo significativamente o consumo de memória e facilitando a análise dos dados.

   Exemplo:

   ![image](https://github.com/user-attachments/assets/247337cb-9585-4def-ae23-24c7835f7859)


3. Uso de Estruturas de Dados Eficientes

    Problema: Armazenar e atualizar grandes volumes de dados pode ser ineficiente se não forem utilizadas estruturas de dados apropriadas.

    Solução: Utilizamos o defaultdict da biblioteca collections para acumular dados de vendas e quantidades. O defaultdict facilita a adição de novos dados sem a necessidade de verificar a existência de chaves, o que simplifica o código e melhora a eficiência do processamento.

   Exemplo:

   ![image](https://github.com/user-attachments/assets/4538f067-bbd9-40fc-951a-5c2be09d93ba)


5. Processamento Incremental e Liberação de Memória

    Problema: O acúmulo de grandes chunks de dados na memória pode levar a problemas de memória se não for gerenciado adequadamente.

    Solução: Após o processamento de cada chunk, a memória alocada é liberada explicitamente usando del para excluir o objeto do chunk e gc.collect() para forçar a coleta de lixo. Isso ajuda a liberar a memória que não é mais necessária e a evitar o crescimento excessivo do uso da memória durante o processamento.

   Exemplo:

   ![image](https://github.com/user-attachments/assets/b5dd7003-0941-48e0-8423-9801c528462d)


7. Análise e Agregação de Dados

    Problema: A análise e agregação de dados em grande escala podem ser desafiadoras, especialmente quando se trabalha com dados distribuídos ao longo de grandes volumes.

    Solução: A agregação e análise de dados são feitas de forma incremental durante o processamento dos chunks. Para identificar o produto mais vendido, o país e a região com o maior volume de vendas, e calcular a média de vendas mensais por produto, utilizamos operações de agregação que são realizadas em cada chunk, acumulando os resultados em estruturas de dados apropriadas.

   Exemplo:

   ![image](https://github.com/user-attachments/assets/fe919eb5-28da-4515-9e9d-75c5eb907240)


# Otimizações de Performance

1. Redução do Tamanho do Chunk: O tamanho do chunk é ajustado para balancear o uso de memória e o desempenho. O valor de 1.000.000 linhas por chunk é um compromisso entre o uso eficiente da memória e a performance. Esse valor pode ser ajustado conforme a capacidade específica da máquina.

2. Eficiência na Manipulação de DataFrames: O uso de parse_dates durante a leitura dos chunks permite que as colunas de datas sejam convertidas diretamente durante a leitura, evitando a necessidade de conversão adicional após a leitura, o que economiza tempo e recursos.

3. Força de Coleta de Lixo: A coleta de lixo manual com gc.collect() ajuda a garantir que a memória seja liberada o mais rápido possível, o que é crucial quando se lida com grandes volumes de dados.

# Conclusão

A solução proposta para o processamento de grandes volumes de dados foi projetada para ser eficiente em termos de memória e desempenho. A leitura em chunks, o uso de estruturas de dados eficientes e a liberação explícita de memória são práticas-chave que garantem que o processamento de dados seja realizado de maneira eficaz, mesmo em máquinas com recursos limitados. Essas abordagens permitem a análise e a agregação de grandes volumes de dados sem comprometer a performance ou causar problemas de memória.
