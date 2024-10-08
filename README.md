# Modelando-dashboard-ecommerce-com-PBI-utilizando-DAX-DesafioBootcampDIO

# Power BI Data Model - Sales Analysis

Este README descreve o modelo de dados utilizado no Power BI para a análise de vendas. O modelo segue a estrutura de um esquema estrela, com uma tabela fato central e tabelas de dimensões conectadas a ela. A tabela fato é a principal fonte de informações para as métricas de desempenho e as dimensões fornecem informações detalhadas sobre diferentes aspectos dos dados de vendas.

## Tabelas Dimensão

- **DimProducts**: Contém detalhes sobre os produtos, incluindo nome, valor de venda e unidades vendidas.
- **DimDiscount**: Detalhes sobre faixas de desconto aplicadas às vendas.
- **DimData**: Fornece informações de data, incluindo ano, mês, semana e dia. Esta tabela foi criada no Power Query usando a linguagem M.
- **DimCountry**: Detalhes sobre os países relacionados às vendas.
- **DimSegment**: Segmenta as vendas com base em diferentes critérios, como o tipo de cliente ou mercado.

## Tabela Fato

- **FactSales**: Esta tabela contém os principais fatos relacionados às vendas, como receita bruta, preço de venda, custo das mercadorias vendidas (COGS), descontos aplicados, e a quantidade de unidades vendidas.

## Tabela Oculta

- **financials_origem**: A tabela de origem oculta no modelo, de onde derivam as demais tabelas, exceto a `DimData`. Ela contém informações brutas como vendas, descontos, preço de manufatura e lucros.

## Tabela de Medidas

- **Medidas**: Tabela exclusiva para medidas calculadas, usadas nas visualizações do Power BI. Essas medidas incluem cálculos de soma, média, entre outros.

## Relacionamentos

A tabela fato `FactSales` é o centro do modelo, conectada a todas as dimensões por meio de chaves estrangeiras. Aqui estão os relacionamentos entre as tabelas:

- **DimProducts** → `FactSales` (via `ID_Product`)
- **DimDiscount** → `FactSales` (via `ID_Discount`)
- **DimData** → `FactSales` (via `Date`)
- **DimCountry** → `FactSales` (via `ID_Country`)
- **DimSegment** → `FactSales` (via `ID_Segment`)

## Esquema Estrela

Abaixo está a representação do modelo em formato estrela:

                  +-----------------+         +-----------------+                       +-----------------+
                  |   DimProducts   |         |   DimDiscount   |                       |financials_origem|
                  +-----------------+         +-----------------+                       +-----------------+      
                           |                           |
                           +-------------+-------------+                                +-----------------+
                                         |                                              |     Medidas     |
                                         |                                              +-----------------+
                                         |
                                +-----------------+                +-----------------+         
                                |    FactSakes    |--------------- |     DimData     |
                                +-----------------+                +-----------------+         
                                         |
                                         |
                                         |
                           +-------------+-------------+
                           |                           |
                    +-----------------+         +-----------------+
                    |    DimCountry   |         |    DimSegment   |
                    +-----------------+         +-----------------+

## Conclusão

Este modelo de dados em Power BI foi criado utilizando o esquema estrela para facilitar a análise de vendas com tabelas de dimensão bem definidas e uma tabela fato centralizada. O uso de medidas calculadas e a criação da `DimData` via Power Query oferecem flexibilidade adicional na análise dos dados.

## Autor

Este projeto foi desenvolvido por Samuel Batista, baseado nas orientações da tutora Juliana Mascarenhas (@julianazanelatto). Sinta-se à vontade para entrar em contato ou contribuir com melhorias!
