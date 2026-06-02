# data-analytics-olist

Análise exploratória do dataset público da **Olist** desenvolvida como Tech Challenge da Fase 1 da pós-graduação em Data Analytics — POSTECH/FIAP.

O objetivo é transformar dados transacionais em insights sobre faturamento, logística e satisfação do cliente, com recomendações práticas para investidores e gestores.

---

## Dataset

[Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — ~99 mil pedidos realizados entre 2016 e 2018, distribuídos em 9 tabelas relacionais.

> O arquivo `olist_geolocation_dataset.csv` não está versionado por ultrapassar o limite de 50MB do GitHub. Baixe diretamente no link acima e coloque na pasta `data/`.

---

## Estrutura do repositório

```
data-analytics-olist/
├── olist_exploratory_analysis.ipynb   ← notebook principal
├── brazil_states.geojson              ← shapefile dos estados (usado no mapa coroplético)
├── README.md
├── .gitignore
├── data/                              ← CSVs do dataset
└── docs/
    └── PDF                            ← Conclusão do projeto
```

---

## O que foi analisado

**Vendas e crescimento**
- Evolução mensal de pedidos e faturamento
- Faturamento trimestral — crescimento de +303% de Q1/2017 a Q2/2018
- Sazonalidade mensal — maio é o pico, setembro o vale
- Top categorias por volume e receita

**Satisfação**
- Distribuição de notas e NPS Simplificado (+34.8)
- Satisfação por categoria ao longo do tempo
- Fotos do produto vs nota do cliente

**Logística**
- Performance de entregas — prazo, atraso e entregas adiantadas
- Gargalo logístico: lead time por etapa (transporte +225% nos atrasos)
- Limiar de tolerância do cliente — ruptura entre 3 e 4 dias de atraso
- Tempo de aprovação do pagamento como elo da cadeia logística
- Boxplot da distribuição do tempo de transporte

**Geografia**
- Mapa coroplético por estado com GeoPandas
- Distância real vendedor→cliente pela fórmula Haversine
- Validação estatística: distância × atraso (r=0.727, p<0.000001)
- Peso do frete por estado

**Clientes e vendedores**
- Taxa de recompra (3.1%) e LTV por segmento
- Frete vs taxa de recompra ao longo do tempo
- Performance dos vendedores — análise de Pareto

**Estatística e previsão**
- Estatística descritiva completa (média, mediana, IQR, outliers)
- Regressão polinomial no ticket mediano com projeção futura (R²=0.455)
- Correlação de Pearson com p-value nas variáveis logísticas

---

## Principais resultados

- Pedidos atrasados têm nota média de **2.46** contra **4.29** dos no prazo — queda de 1.83 pontos
- O **transporte** é o gargalo: vai de 7.9 dias (no prazo) para 25.7 dias nos atrasados (+225%)
- O cliente perde a tolerância a partir de **3 dias de atraso** — acima disso a nota cai abruptamente
- Distância × atraso: r=0.727 | Distância × nota: r=−0.646 — ambos estatisticamente comprovados
- **96.9%** dos clientes compram apenas uma vez — LTV médio de R$161 vs R$291 para quem volta
- SP concentra 42% dos pedidos; Norte e Nordeste têm frete acima de 25% do valor do produto

---

## Como executar

```bash
# Clonar o repositório
git clone https://github.com/juansouzamd/data-analytics-olist.git
cd data-analytics-olist

# Instalar dependências
pip install pandas numpy matplotlib seaborn geopandas scipy

# Abrir o notebook
jupyter notebook olist_exploratory_analysis.ipynb
```

Coloque os CSVs do dataset na pasta `data/` antes de rodar.

---

## Tecnologias

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `GeoPandas` · `SciPy` · `Jupyter`

---

**POSTECH Data Analytics — Fase 1 · Tech Challenge · 2026**
