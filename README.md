# Dashboard-SuperStore
# Superstore 360° — Análise de Vendas, Rentabilidade e Logística com Power BI

## 💡 Resumo do projeto

Este projeto apresenta um dashboard interativo desenvolvido em Power BI com foco na análise de vendas, lucro, prejuízo, descontos e desempenho logístico da base Superstore. O objetivo foi transformar dados comerciais em insights estratégicos para apoiar decisões sobre faturamento, rentabilidade, produtos deficitários e eficiência operacional.

O projeto foi estruturado como um painel executivo, simulando uma análise real de negócio para identificar onde a empresa vende mais, onde perde dinheiro e quais fatores podem impactar sua margem.

---

## ❓ Problema de negócio / contexto

Empresas que possuem grande volume de vendas nem sempre conseguem transformar faturamento em lucro. Alguns produtos, categorias, regiões ou políticas de desconto podem gerar prejuízo mesmo com alto volume comercial.

Este projeto busca responder perguntas como:

* Quais regiões geram mais faturamento?
* Quais categorias e produtos concentram maior lucro ou prejuízo?
* O desconto aplicado está impactando negativamente a rentabilidade?
* Existe relação entre tempo de entrega e lucro?
* Quais regiões ou modos de envio apresentam maior tempo médio de entrega?
* Quais indicadores devem ser acompanhados em um painel executivo?

---

## 📊 Dados utilizados

A base utilizada foi o dataset **Sample Superstore**, contendo informações comerciais de pedidos, clientes, produtos, regiões, vendas, descontos, lucro e envio.

Principais colunas utilizadas:

* `Order Date`
* `Ship Date`
* `Ship Mode`
* `Segment`
* `Region`
* `State`
* `Category`
* `Sub-Category`
* `Product Name`
* `Sales`
* `Quantity`
* `Discount`
* `Profit`

Durante a validação dos dados, foi identificado que a coluna `Sales` já representa o valor total da venda por linha. Por isso, o faturamento foi calculado pela soma direta de `Sales`, evitando duplicidade ao multiplicar por `Quantity`.

---

## 🛠️ Metodologia e ferramentas

### Ferramentas utilizadas

* Power BI
* Power Query
* DAX
* Excel/CSV
* Análise exploratória de dados
* Estatística descritiva
* Storytelling com dados

### Etapas do projeto

1. Importação do dataset no Power BI.
2. Tratamento e validação dos dados no Power Query.
3. Criação de colunas auxiliares, como tempo de entrega e faixas de entrega.
4. Desenvolvimento de medidas DAX para faturamento, lucro, prejuízo, margem e indicadores logísticos.
5. Construção de dashboards temáticos:

   * Faturamento
   * Lucro vs Prejuízo
   * Logística e Entregas
   * Descontos e Rentabilidade
   * Resumo Executivo
6. Criação de insights de negócio e recomendações estratégicas.

---

## 📌 Principais medidas DAX

### Faturamento Total

```DAX
Faturamento Total =
SUM('superstore'[Sales])
```

### Lucro Total

```DAX
Lucro Total =
SUM('superstore'[Profit])
```

### Margem de Lucro

```DAX
Margem de Lucro =
DIVIDE(
    [Lucro Total],
    [Faturamento Total]
)
```

### Lucro Positivo

```DAX
Lucro Positivo =
CALCULATE(
    SUM('superstore'[Profit]),
    'superstore'[Profit] > 0
)
```

### Prejuízo Total

```DAX
Prejuízo Total =
ABS(
    CALCULATE(
        SUM('superstore'[Profit]),
        'superstore'[Profit] < 0
    )
)
```

### Total de Pedidos

```DAX
Total Pedidos =
DISTINCTCOUNT('superstore'[Order ID])
```

### Tempo Médio de Entrega

```DAX
Tempo Médio Entrega =
AVERAGE('superstore'[DiasEntrega])
```

### Lucro Médio

```DAX
Lucro Médio =
AVERAGE('superstore'[Profit])
```


---

## 📈 Principais insights e resultados

### 1. Faturamento concentrado por região

A análise de faturamento mostra que determinadas regiões concentram maior participação nas vendas. Esse resultado permite identificar quais mercados possuem maior relevância comercial e onde a empresa pode direcionar estratégias de expansão ou manutenção.

**Recomendação:** acompanhar o desempenho regional de forma contínua para entender onde há maior potencial de crescimento.

---

### 2. Alto faturamento não garante maior lucro

O projeto evidencia que vender mais nem sempre significa obter melhor resultado financeiro. Algumas categorias e produtos apresentam baixo lucro ou até prejuízo, mesmo com volume relevante de vendas.

**Recomendação:** analisar produtos deficitários e revisar estratégias de preço, margem e desconto.

---

### 3. Produtos com prejuízo devem ser monitorados

A análise de lucro vs prejuízo permite identificar produtos e subcategorias que impactam negativamente o resultado da empresa.

**Recomendação:** criar uma rotina de acompanhamento dos produtos com maior prejuízo e avaliar ações como renegociação, redução de desconto ou descontinuação.

---

### 4. Descontos elevados impactam a rentabilidade

A análise entre `Discount` e `Profit` indica que descontos mais altos tendem a reduzir o lucro médio e aumentar o risco de prejuízo.

**Recomendação:** revisar a política de descontos, principalmente em categorias com baixa margem.

---

### 5. Logística influencia a análise operacional

Com base na diferença entre data do pedido e data de envio, foi possível analisar o tempo médio de entrega por região e modo de envio.

**Recomendação:** investigar regiões e métodos de envio com maior tempo médio, buscando reduzir gargalos logísticos.

---

### 6. Estatística descritiva como apoio à análise

Foram utilizadas medidas como média, mediana, desvio padrão e coeficiente de variação para entender melhor a distribuição do lucro.

**Recomendação:** utilizar estatística descritiva para identificar dispersão, assimetria e possíveis outliers nos resultados financeiros.

---

## 🧠 Resumo executivo

A análise integrada de vendas, lucro, prejuízo, descontos e logística mostra que o aumento do faturamento não garante maior rentabilidade. O projeto evidencia a importância de acompanhar margem, produtos deficitários, política de descontos e eficiência operacional.

A empresa pode melhorar seus resultados ao revisar produtos com prejuízo recorrente, controlar descontos elevados e monitorar regiões ou modos de envio com maior tempo médio de entrega.

---

## 📊 Dashboards desenvolvidos

### 1. Dashboard de Faturamento

Análise do desempenho comercial por região, categoria, estado e período.

### 2. Dashboard de Lucro vs Prejuízo

Identificação de produtos, categorias e regiões que geram lucro ou prejuízo.

### 3. Dashboard de Logística e Entregas

Análise de tempo médio de entrega, modo de envio, pedidos por mês e gargalos regionais.

---

## 🚀 Como executar o projeto

1. Baixe o arquivo `.pbix` disponível neste repositório.
2. Abra o arquivo no Power BI Desktop.
3. Verifique o caminho da base de dados, caso seja necessário atualizar a fonte.
4. Atualize os dados.
5. Navegue pelas páginas do dashboard utilizando os filtros interativos.

---



## 📸 Prévia do dashboard

Adicione aqui imagens do seu projeto:

```markdown

![Dashboard de Faturamento](images/analise_faturamento.png)

![Dashboard de Lucro vs Prejuízo](images/analise_lucroxpreju.png)

![Dashboard de Logística](images/analise_logistica.png)

```

---

## 📚 Aprendizados

Durante o desenvolvimento deste projeto, foram praticados conceitos importantes para análise de dados e Business Intelligence, como:

* Validação de métricas;
* Tratamento de dados no Power Query;
* Criação de medidas DAX;
* Construção de dashboards interativos;
* Análise de faturamento, lucro e prejuízo;
* Análise logística;
* Estatística descritiva;
* Storytelling com dados;
* Geração de insights de negócio.

---

## 🏷️ Tags

`Power BI` `Business Intelligence` `DAX` `Power Query` `Análise de Dados` `Dashboard` `Superstore` `Estatística Descritiva` `Portfólio de Dados`
