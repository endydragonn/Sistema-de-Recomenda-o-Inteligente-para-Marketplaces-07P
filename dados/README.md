# Documentação dos Dados (Datasets)

Esta pasta contém as bases de dados utilizadas para o treinamento e validação do Sistema de Recomendação Inteligente. 

## Origem dos Dados
Os dados brutos (`olist_...`) foram extraídos do **Brazilian E-Commerce Public Dataset by Olist**, disponível publicamente no Kaggle. Eles representam transações reais de e-commerce brasileiro entre 2016 e 2018.

## Descrição dos Arquivos Brutos
* **`olist_orders_dataset.csv`**: Tabela mestre de pedidos (contém IDs de pedido e IDs de cliente).
* **`olist_order_items_dataset.csv`**: Detalhes dos itens (liga o pedido ao produto específico).
* **`olist_order_reviews_dataset.csv`**: Contém as avaliações e notas (1 a 5) dadas pelos clientes.

## O Dataset Preparado (`dataset_preparado.csv`)
Este arquivo **não é baixado**, ele é gerado pelo notebook `01_analise_exploratoria_N1.ipynb`. Ele consolida as informações essenciais para a Inteligência Artificial:

| Coluna | Descrição |
| :--- | :--- |
| `user_idx` | ID do usuário mapeado para um índice numérico (0, 1, 2...). |
| `item_idx` | ID do produto mapeado para um índice numérico (0, 1, 2...). |
| `review_score` | Nota da avaliação (Target do nosso modelo de Deep Learning). |

## Processamento Realizado
1. **União (Merge):** Cruzamento das tabelas de pedidos, itens e avaliações.
2. **Limpeza:** Remoção de dados faltantes (NaN).
3. **Encoding:** Conversão de IDs alfanuméricos longos em índices numéricos densos para alimentar as camadas de *Embedding* do modelo.
