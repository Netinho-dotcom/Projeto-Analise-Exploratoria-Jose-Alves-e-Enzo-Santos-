# Análise e Pré‑Processamento do Dataset Olist E‑Commerce
**Disciplina:** Ciência de Dados  
**Curso:** Engenharia de Software  
**Instituição:** Centro Universitário Santo Agostinho  
**Ano:** 2025  

## 👥 Integrantes
- **José Alves Lima Neto**  
- **Enzo Santos Silva**

## 🔗 Base de Dados Utilizada
O projeto utiliza o **Olist Brazilian E‑Commerce Public Dataset**, disponível no Kaggle:  
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Bases usadas:  
- olist_orders_dataset.csv  
- olist_order_items_dataset.csv  
- olist_products_dataset.csv

## 🎯 Objetivo do Projeto
Entender **quais fatores influenciam a experiência e satisfação do cliente** no e‑commerce brasileiro, analisando:  
- atrasos,  
- logística,  
- características dos produtos,  
- preços e fretes,  
- prazos estimados vs reais.

## 🔧 Tratamento dos Dados

### 1. Importação e Integração
- Carregamento das bases utilizando pandas.
- Junção via `order_id` e `product_id`, formando a base principal.

### 2. Limpeza de Dados
- Remoção de itens sem medidas físicas.  
- Preenchimento de categorias ausentes com `"unknown"`.  
- Manutenção de datas vazias (representam status real).  
- Remoção de pedidos sem itens.

### 3. Outliers
- Detecção via IQR.  
- Outliers logísticos reais foram mantidos.  
- Valores irreais foram capados.

### 4. Padronização de Tipos
- Datas → `datetime`  
- Numéricos → `float`/`int`  
- IDs → `string`  
- Categorias → `category`

### 5. Normalização e Padronização
- Min-Max (0–1)  
- Z-score  
- Variáveis originais preservadas.

### 6. Codificação de Variáveis
- Agrupamento das categorias menos frequentes em `"other"`.  
- One-Hot Encoding com `drop_first=True`.

### 7. Feature Engineering
- `approval_delay_hours`  
- `delivery_time_days`  
- `estimated_to_actual_days`  
- `is_free_shipping`  
- `price_per_gram`

### 8. Pipeline Final
- Organização das etapas em pipeline para reprodutibilidade.

## 🧩 Desafios Encontrados
- Muitos valores ausentes em etapas importantes.  
- Produtos sem medidas físicas.  
- Muitas categorias diferentes.  
- Outliers legítimos precisando ser preservados.  
- Harmonização de datas e tipos antes da análise.  
- Volume grande de dados exigindo cuidado com performance.

## 📈 Principais Conclusões

### 1. Entregas têm alta variabilidade
Prazos muito diferentes devido a fatores logísticos.

### 2. Algumas categorias atrasam mais
Itens grandes/pesados são mais lentos.

### 3. Frete e preço não determinam velocidade
Produtos caros não chegam mais rápido.

### 4. Frete depende mais do volume do produto
Dimensões influenciam mais que preço.

### 5. Atrasos ocorrem em várias etapas
Aprovação → preparo → expedição → transporte.

### 6. Novas variáveis revelaram padrões
Feature engineering ampliou a análise.

## 📜 Conclusão Geral
A análise aprofundada do dataset da Olist permitiu compreender de forma clara como diferentes fatores influenciam a experiência do cliente no e‑commerce brasileiro. Observou‑se que o processo logístico desempenha um papel central na satisfação do consumidor, sendo responsável pela maior parte dos atrasos e inconsistências na entrega. Produtos com características físicas mais complexas — como dimensões grandes, peso elevado ou volume fora do padrão — apresentaram maior probabilidade de gerar atrasos, evidenciando a necessidade de melhorias específicas no armazenamento e transporte desses itens.

Além disso, verificou-se que o preço do produto e o valor do frete não são bons indicadores de velocidade de entrega, quebrando um senso comum importante. A eficiência operacional se mostrou mais determinante que o custo envolvido na compra. A etapa de aprovação do pagamento e a preparação interna dos pedidos também contribuíram significativamente para atrasos, mostrando que o problema não está restrito ao transporte, mas a todo o fluxo da cadeia logística.

O tratamento dos dados — incluindo limpeza, padronização, identificação de outliers e criação de novas variáveis — revelou padrões que não eram visíveis no conjunto de dados bruto. As variáveis construídas ajudaram a entender gargalos específicos e contribuíram para análises mais precisas e interpretáveis.

Por fim, conclui‑se que a experiência do cliente no e‑commerce depende de uma combinação de fatores, com forte predominância dos elementos logísticos e operacionais. Investimentos em automação, melhor integração entre fornecedores, padronização de embalagens e otimização nas etapas internas podem reduzir atrasos e melhorar significativamente a percepção do consumidor. O estudo destaca a importância da gestão eficiente da cadeia de suprimentos como elemento estratégico para competitividade no mercado digital.

