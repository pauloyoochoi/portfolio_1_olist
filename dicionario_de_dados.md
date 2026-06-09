# Dicionário de dados

Este documento descreve as variáveis das duas tabelas do dataset Marketing Funnel da Olist. A chave que liga as duas tabelas é a coluna `mql_id`.

## Tabela: olist_marketing_qualified_leads_dataset

Cada linha representa um lead qualificado pelo marketing (MQL).

| Coluna | Descrição | Tipo | Valores possíveis |
|---|---|---|---|
| `mql_id` | Identificador único do lead. Chave de ligação com a tabela de negócios fechados. | Identificador (texto) | Código único por lead |
| `first_contact_date` | Data da primeira solicitação de contato do lead. | Data | Datas no formato AAAA-MM-DD |
| `landing_page_id` | Identificador da landing page onde o lead foi captado. | Identificador (texto) | Código único por landing page |
| `origin` | Tipo de mídia (canal) por onde o lead foi adquirido. | Categórica | organic_search, paid_search, social, direct_traffic, email, referral, display, other, other_publicities, unknown |

## Tabela: olist_closed_deals_dataset

Cada linha representa um negócio fechado (um lead que virou cliente).

| Coluna | Descrição | Tipo | Valores possíveis |
|---|---|---|---|
| `mql_id` | Identificador do lead que originou o negócio. Chave de ligação com a tabela de leads. | Identificador (texto) | Código único por lead |
| `seller_id` | Identificador do vendedor (lojista). | Identificador (texto) | Código único por vendedor |
| `sdr_id` | Identificador do Sales Development Representative (SDR), responsável pela qualificação inicial. | Identificador (texto) | Código único por SDR |
| `sr_id` | Identificador do Sales Representative (SR), responsável pelo fechamento. | Identificador (texto) | Código único por SR |
| `won_date` | Data e hora em que o negócio foi fechado. | Data e hora | Data e hora do fechamento |
| `business_segment` | Segmento de negócio do lead, informado no contato. | Categórica | Diversos segmentos de varejo, como pet, home_decor, health_beauty, car_accessories, household_utilities |
| `lead_type` | Tipo do lead, ligado ao porte e à maturidade digital. Informado no contato. | Categórica | online_medium, online_big, online_small, online_beginner, online_top, industry, offline, other |
| `lead_behaviour_profile` | Perfil comportamental do lead, identificado pelo SDR no contato. | Categórica | cat, eagle, wolf, shark (e combinações entre eles) |
| `has_company` | Indica se o lead possui empresa formalizada. | Booleana | True, False |
| `has_gtin` | Indica se o lead possui GTIN (código de barras) para os produtos. | Booleana | True, False |
| `average_stock` | Estoque médio declarado pelo lead, informado no contato. | Categórica (faixas) | Faixas de quantidade em texto (ex.: "20-50") |
| `business_type` | Tipo de negócio do lead. | Categórica | reseller, manufacturer, other |
| `declared_product_catalog_size` | Tamanho do catálogo de produtos declarado pelo lead. | Numérica | Número (quantidade de produtos) |
| `declared_monthly_revenue` | Receita mensal estimada declarada pelo lead. | Numérica | Número (valor estimado) |
