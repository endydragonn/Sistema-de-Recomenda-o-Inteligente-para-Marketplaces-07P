# Descrição do Dataset

O projeto utiliza o **Brazilian E-Commerce Public Dataset by Olist**, um conjunto de dados reais, anonimizados e cedidos pela Olist para a comunidade acadêmica via Kaggle.

## Origem e Contexto
* **Fonte:** [Kaggle - Olist Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data)
* **Período:** Compras realizadas entre 2016 e 2018 em diversos marketplaces no Brasil.
* **Volume:** Aproximadamente 100 mil pedidos.

## Estrutura dos Arquivos Originais Utilizados
Para a construção do modelo de recomendação, realizamos o cruzamento (*merge*) das seguintes tabelas:

1.  `olist_orders_dataset.csv`: Contém o ID do pedido e o ID do cliente.
2.  `olist_order_items_dataset.csv`: Relaciona os pedidos aos IDs dos produtos.
3.  `olist_order_reviews_dataset.csv`: Contém a nota de avaliação (*review score*) de 1 a 5 dada pelo consumidor.

## Dataset Preparado (`dataset_preparado.csv`)
Após a etapa de análise exploratória e limpeza de dados (N1), geramos um arquivo consolidado para o treinamento da Inteligência Artificial com as seguintes colunas:

| Coluna | Descrição |
| :--- | :--- |
| `user_idx` | Índice numérico inteiro que representa o cliente único (gerado via LabelEncoding). |
| `item_idx` | Índice numérico inteiro que representa o produto único (gerado via LabelEncoding). |
| `review_score` | A variável alvo (Label). Nota de 1 a 5 atribuída pelo usuário ao item. |

## Tratamentos Realizados
* **Limpeza:** Remoção de registros com valores nulos nas colunas de interação.
* **Filtro:** Cruzamento de tabelas para garantir que apenas pedidos com avaliações válidas fossem utilizados.
* **Engenharia de Atributos:** Transformação de IDs hexadecimais complexos em índices numéricos sequenciais para otimizar o processamento das camadas de *Embedding* do TensorFlow.
