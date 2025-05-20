# Governança-e-Data-Quality-com-Great-Expectations

📚 Neste projeto vamos estudar um importante tema no universo dos Data Warehouses: a governança de dados através dos testes de qualidade.

🧩 O que é governança de dados?

Governança de Dados é um conjunto de processos, políticas, normas e responsabilidades que visam garantir a qualidade, segurança, integridade e uso adequado dos dados em uma organização.

Ela estabelece quem pode acessar, modificar, compartilhar ou excluir dados, além de definir padrões para sua coleta, armazenamento e análise.

🛠 Principais Objetivos da Governança de Dados:

1. Qualidade dos Dados – Garantir que os dados sejam precisos, consistentes e confiáveis.

2. Conformidade – Cumprir leis e regulamentos (como LGPD, GDPR).

3. Segurança – Proteger dados contra vazamentos e acessos não autorizados.

4. Eficiência – Melhorar a tomada de decisão com dados bem gerenciados.

5. Responsabilidade – Definir papéis (como DPO, stewards de dados) para supervisionar os dados.


🧩 O que é qualidade de dados (data quality)

Qualidade de dados (data quality) é a medida de quão adequados os dados são para seu uso pretendido, ou seja, se eles são precisos, completos, consistentes, atualizados, válidos e disponíveis quando necessários.

🛠 Principais dimensões da qualidade de dados:

1. Precisão
   
Os dados refletem corretamente a realidade?

2. Completude
   
Todos os campos essenciais estão preenchidos?

3. Consistência
   
Os dados são coerentes entre diferentes sistemas ou registros?

4. Atualização
   
Os dados estão atualizados e disponíveis no tempo certo?

5. Validade
   
Os dados seguem os formatos e regras definidos?

6. Unicidade

Não há duplicações desnecessárias?


🧩 O que é e quando usamos a ferramenta Great Expectations?

A ferramenta Great Expectations é uma plataforma de validação de qualidade de dados automatizada. Ela permite que você crie testes automatizados para verificar se os dados estão corretos, completos, consistentes, válidos, etc. antes de usá-los em relatórios, análises ou cargas de dados (ETL/ELT).

🛠 Quando usar o Great Expectations?

Use quando você precisa de:

1. Validação automatizada de dados
   
Antes de carregar dados em um data warehouse ou alimentar dashboards, valide se os dados estão corretos.

2. Testes em pipelines de dados (ETL/ELT)
   
Integre com Airflow, dbt, Dagster, Prefect, etc., para interromper o pipeline se houver erro.

3. Auditoria e rastreabilidade (Data Quality Checks)
   
Gere documentação automática sobre as regras de qualidade e os resultados dos testes.

4. Detecção precoce de anomalias
   
Encontre valores inesperados antes que causem problemas em relatórios ou decisões.


🔧 Programas que irei utilizar:

✅ Grrreat Expectations

✅ Docker

✅ Anaconda Python

✅ PgAdmin


📚 Vamos começar o projeto com os arquivos da qualidade de dados:

![image](https://github.com/user-attachments/assets/4a9d0872-5a1f-49e2-928f-6f45bad7ebdc)

🧩 Este script está utilizando a biblioteca Great Expectations (GX) para realizar validações de qualidade de dados em um arquivo CSV chamado dataset.csv.

🔍 Pontos-Chave:

1. Validação Estrutural

* Verificou a existência da coluna id, a contagem de colunas (1–3) e linhas (1–100).

2. Validação de Conteúdo

* Confirmou que os valores de id são únicos, não nulos e estão entre 1 e 10.

3. Documentação e Auditoria

* Salvou as expectativas em um "expectation suite" para reuso.

* Gerou um relatório detalhado (HTML) com resultados das validações.

4. Automação

* Usou um checkpoint (dsa_checkpoint) para executar todas as validações de forma reproduzível.

🔍 Resultado Final:

* Se Resultado da Análise: True → Todos os critérios foram atendidos.

* Se False → Alguma expectativa falhou (ex.: id fora do intervalo ou duplicado), exigindo correção nos dados ou ajuste nas regras.

🔍 Por que isso é importante?

* Evita erros em análises ou processos downstream (ex.: relatórios com dados inconsistentes).

* Reduz riscos de conformidade (ex.: violação de LGPD por dados duplicados).

* Economiza tempo com validações automatizadas em vez de verificações manuais.

🔍 Próximos Passos:

* Adapte as expectativas para outros datasets (ex.: validar e-mails, CPFs, datas).

* Integre o script a um pipeline de dados (ex.: Airflow, Prefect) para validações contínuas.

Em resumo, o GX transforma qualidade de dados de um desafio manual em um processo confiável, escalável e documentado.


📚 Agora vamos executar, navegar até a pasta onde está salvo e instalar o pacote pelo prompt de comando do Anaconda Python, e iniciar o Python dataquality.py diretamente pelo navegador web.

![Image](https://github.com/user-attachments/assets/a7c3c86f-f61b-47fc-9ad9-07ad0ed09059)

🧩 Calculando as metricas:

![image](https://github.com/user-attachments/assets/27012703-a9bb-4392-a495-22f751bf22d2)


🧩 Resultado da análise:

![Image](https://github.com/user-attachments/assets/8a1974f3-714f-4d39-8f43-c31f36e3496e)


🧩 Table Level Expectations:

![Image](https://github.com/user-attachments/assets/1613d8e3-05ed-4fd3-b4c6-d5d9475de095)


📚  Processo de Governança e Qualidade de Dados no Data Warehouse

Aqui vamos construir uma das principais etapas do processo de governança de dados: o processo de validação da qualidade dos dados. E faremos isso trabalhando com o Great Expectations, ferramenta que permite automatizar a validação de expectativas e checagem de regras de negócio. Primeiro vamos preparar o Docker (script e comandos na pasta do projeto).

![Image](https://github.com/user-attachments/assets/1af29bc1-aa92-423c-9172-fba3b8c1c7b0)


Feito isso, vamos para o PgAdmin registrar o servidor e executar os dois scripts para criar o DW, com suas dimensões e a tabela fato:

![Image](https://github.com/user-attachments/assets/d76f76e9-ade8-4d05-8ff7-e739177e6d42)


Agora vamos trabalhar com os scripts Python que farão a checagem de qualidade de dados no Data Warehouse

![Image](https://github.com/user-attachments/assets/6d6adcfd-1e41-4070-9d3c-09a990464bba)


🔧 Configurando a conexão ao SGBD com linguagem Python (lab4.py, 02-modelo-fisico-prrojeto1.sql e 03-processo_etl.sql)

Este script implementa um processo completo de validação de qualidade de dados em um Data Warehouse com PostgreSQL, utilizando a biblioteca Great Expectations. Ele é um exemplo prático de governança de dados aplicada, onde a consistência, completude e conformidade dos dados são verificadas antes de serem utilizados para análise ou tomada de decisão.

🔍 O que está acontecendo no script:

1. Conexão com o PostgreSQL:

* O script define a string de conexão e configura o datasource do banco de dados no Great Expectations.
  

2. Criação de um processo de validação genérico:

* Uma função (dsa_valida_expectativas) é criada para aplicar conjuntos de expectativas a qualquer tabela do schema dw (Data Warehouse).

* A validação retorna o resultado e gera um relatório em HTML.
  

3. Validações específicas por tabela:

🔹 São definidas expectativas (regras) para as seguintes tabelas:

* dim_produto

* dim_canal

* dim_cliente

* fato_venda

🔹 Exemplos de expectativas:

* Verificar existência de colunas.

* Garantir valores não nulos.

* Garantir unicidade de valores (como chaves primárias).

* Validar faixas de valores (quantidade entre 1 e 1000).

* Verificar domínios de valores (por exemplo, categorias válidas ou tipos de clientes).
  

4. Geração de relatórios de validação:

* Um relatório em formato HTML é gerado para cada tabela, com os resultados das validações — útil para auditoria e acompanhamento visual da qualidade.


🧩 Hora de executar os arquivos:

![Image](https://github.com/user-attachments/assets/411fa0e3-8b12-4b4e-a752-dc41b97a8917)


* E então executar o laboratório ou script da Lab:

![Image](https://github.com/user-attachments/assets/b78d441a-f327-49b7-b24c-de77cd9aede9)

* Geração de relatórios:

![Image](https://github.com/user-attachments/assets/3dc73a42-83bb-405e-ba00-0dd1bbf33f8d)

![Image](https://github.com/user-attachments/assets/1adfc802-524d-4e0d-939a-b7e54638e26a)


✅ Conclusão

Neste projeto, exploramos como a governança e a qualidade de dados são pilares fundamentais em ambientes de Data Warehouse. Utilizando ferramentas modernas como o Great Expectations, mostramos na prática como automatizar testes, garantir conformidade com regras de negócio e aumentar a confiabilidade dos dados.

Ao transformar processos manuais em validações automatizadas, ganhamos eficiência, reduzimos riscos e criamos uma base sólida para análises e decisões estratégicas. Essa abordagem é essencial para qualquer organização que deseje escalar suas operações de dados com segurança e qualidade.




