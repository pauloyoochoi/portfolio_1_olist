# Análise do Funil de Marketing da Olist

Projeto de Analytics Engineering que analisa o funil de captação de vendedores da Olist, do primeiro contato do lead até o fechamento do negócio, usando SQL no Databricks e um modelo de dados em camadas.

## Sobre a empresa

A Olist é um ecossistema brasileiro de tecnologia para o varejo que conecta e centraliza a gestão de lojistas em diferentes canais de venda, como marketplaces, e-commerces e lojas físicas.

Seu crescimento depende da aquisição contínua de novos lojistas, que chegam por meio de canais de marketing e aquisição. Após o primeiro contato, esses potenciais clientes passam por etapas de qualificação conduzidas pela equipe comercial, até avançarem no funil de vendas, formalizarem a contratação e passarem a integrar o ecossistema da Olist.

## Perguntas

Com base nos dados disponibilizados pela Olist na plataforma Kaggle, este projeto tem como objetivo avaliar a eficiência do funil de marketing e vendas da empresa, da origem dos leads até a sua conversão em clientes. O estudo também caracteriza o perfil dos lojistas adquiridos.

A análise foi organizada para responder a cinco perguntas:
1. Qual canal de origem converte mais leads em vendas?
2. Quanto tempo cada canal leva até fechar?
3. A conversão é rápida e estável ao longo dos meses?
4. O perfil dos vendedores captados mudou ao longo de 2018?
5. O porte do vendedor se relaciona com ele fabricar ou revender?

## Stack

- Databricks (Unity Catalog) como ambiente de dados
- SQL para toda a transformação e análise
- Modelagem em camadas (staging, intermediate, mart), no estilo dbt
- Git e GitHub para versionamento
- Metabase para o dashboard de BI

## Estrutura do projeto

O projeto segue uma sequência:

- Exploração inicial: estrutura das tabelas (quantidade de linhas e colunas, dicionário de dados, tipos de respostas e exploração de uma amostra dos registros).
- Verificação da qualidade dos dados: auditoria das tabelas para identificar duplicatas, valores ausentes e inconsistências.
- Análise descritiva: descrição de cada variável a partir de suas distribuições e padrões gerais.
- Modelagem dos dados: a camada de transformação, dividida em
  - staging: limpeza e padronização de cada tabela.
  - intermediate: junção das tabelas.
  - mart: base final para análises e dashboard.
- Análise: as respostas das cinco perguntas, com gráficos e leitura de negócio.

## Principais resultados

- Os melhores canais são paid_search (12,3%), organic_search (11,8%) e direct_traffic (11,2%), todos acima da média de 10,5%. Já social (5,6%) e email (3,0%) têm os piores resultados. Apesar do alto volume de leads em social, a conversão é baixa, indicando ineficiência. O grupo nao_identificado apresenta a maior taxa (16,7%), mas não é acionável e sugere falhas de rastreamento.
- O tempo médio de fechamento é de 14 dias. Paid_search, organic_search e direct_traffic fecham mais rápido, entre 10 e 15 dias. Já social (30 dias) e email (21 dias) levam mais tempo para converter.
- A conversão é rápida: cerca de dois terços dos negócios se concretizam em até 30 dias, com poucos casos mais longos. A série de conversão apresenta um pico ao final de 2017 e uma leve queda na coorte de maio de 2018, sugerindo variações pontuais ao longo do período.
- Não houve mudança relevante no perfil dos leads convertidos. Predominam os online_medium, seguidos por online_big, industry e offline, com distribuição estável ao longo de 2018.
- Em geral, predominam resellers, enquanto manufacturers aparecem mais no segmento industry. Nos perfis online, há uma leve tendência de menos fabricantes em portes maiores, mas sem um padrão consistente.

Os resultados estão consolidados em um dashboard interativo no Metabase, com os cinco gráficos que respondem às perguntas do projeto. https://balmy-tarpon.metabaseapp.com/public/dashboard/8eda8f56-c7d6-42ae-a27e-aaf25b14f58a

## Recomendações

- Corrigir o rastreamento de origem: como o maior conversor é o grupo sem origem identificada (16,7%), melhorar o tracking permitiria direcionar melhor o investimento.
- Usar o tempo típico de fechamento, com a maioria em até 30 dias, como referência para priorizar o follow-up de leads que extrapolam essa janela.

## Limitações

- O perfil do vendedor só existe para os 842 negócios fechados, não para os 8000 leads, então as análises de perfil descrevem quem converteu, não o total captado.
- Colunas importantes foram descartadas por estarem quase vazias ou imprestáveis (declared_monthly_revenue com 95% de zeros, declared_product_catalog_size com 69 preenchidos, has_company e has_gtin com 92% de nulos).
- Os dados cobrem um período específico de uma operação ainda em maturação, então as conclusões podem não valer para períodos posteriores.

## Dados

Olist Marketing Funnel Dataset, disponível publicamente no Kaggle. https://www.kaggle.com/datasets/olistbr/marketing-funnel-olist
