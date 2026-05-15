# Problema Analítico: Disponibilidade e Distribuição de Leitos Hospitalares

## 1 Objetivo

> **Analisar** a infraestrutura hospitalar registrada no indicador REC.2.01,  
> **com o propósito de** diagnosticar a disponibilidade e a distribuição de leitos hospitalares no SUS e na rede privada,  
> **com foco em** leitos gerais, UTIs e UCIs por tipo de atendimento, esfera administrativa e perfil populacional,  
> **do ponto de vista de** gestores públicos de saúde, pesquisadores e planejadores hospitalares,  
> **no contexto de** dados históricos municipais de leitos hospitalares do DATASUS/RIPSA a partir de 2006.  

---

# 2 Questões

> **Q1:** Qual a disponibilidade de leitos hospitalares por município?  
> - **H1:** Existe desigualdade significativa na quantidade de leitos entre municípios.  
> - **H2:** Municípios mais populosos possuem maior densidade de leitos por habitante.  

---

> **Q2:** Como está distribuída a oferta de leitos entre SUS e não SUS?  
> - **H1:** A maior parte dos leitos especializados está concentrada na rede não SUS.  
> - **H2:** Municípios menores dependem proporcionalmente mais de leitos públicos vinculados ao SUS.  

---

> **Q3:** Qual é a disponibilidade de leitos especializados (UTI/UCI) por faixa populacional?  
> - **H1:** Leitos neonatais e pediátricos estão concentrados em municípios de maior porte.  
> - **H2:** Existe baixa cobertura de UTI adulto em municípios pequenos e médios.  

---

> **Q4:** Como os leitos estão distribuídos entre rede pública e privada?  
> - **H1:** Municípios economicamente mais desenvolvidos possuem maior participação de leitos privados.  
> - **H2:** A rede pública concentra a maior parte dos leitos SUS.  

---

# 3 Métricas

## Métrica 1 — Taxa de Leitos por 1.000 Habitantes

> **Descrição:** Calcula a quantidade de leitos hospitalares disponíveis para cada mil habitantes.  

> **Fórmula:**  

\[
\frac{\text{Nº total de leitos}}{\text{População total}} \times 1000
\]

> **Medidas:**  
> - Nº total de leitos  
> - População total  

> **Unidade:**  
> - Leitos por 1.000 habitantes  

> **Granularidade:**  
> - Municipal  
> - Anual  

---

## Métrica 2 — Proporção de Leitos SUS

> **Descrição:** Mede a participação dos leitos SUS em relação ao total de leitos disponíveis.  

> **Fórmula:**  

\[
\frac{\text{Nº leitos SUS}}{\text{Nº total de leitos}} \times 100
\]

> **Medidas:**  
> - Nº leitos SUS  
> - Nº total de leitos  

> **Unidade:**  
> - Percentual (%)  

> **Granularidade:**  
> - Municipal  
> - Anual  

---

## Métrica 3 — Índice de Especialização Hospitalar

> **Descrição:** Mede a presença de leitos especializados de alta complexidade no município.  

> **Fórmula:**  

\[
\text{UTI adulto} + \text{UTI neonatal} + \text{UTI pediátrica} + \text{UTI coronariana}
\]

> **Medidas:**  
> - Nº de leitos UTI/UCI por categoria  

> **Unidade:**  
> - Quantidade de leitos especializados  

> **Granularidade:**  
> - Municipal  

---

## Métrica 4 — Participação da Rede Privada

> **Descrição:** Mede a participação dos leitos privados em relação ao total de leitos hospitalares.  

> **Fórmula:**  

\[
\frac{\text{Nº total de leitos privados}}{\text{Nº total de leitos}} \times 100
\]

> **Medidas:**  
> - Nº total de leitos privados  
> - Nº total de leitos  

> **Unidade:**  
> - Percentual (%)  

> **Granularidade:**  
> - Municipal  
> - Anual  

---

## Métrica 5 — Cobertura Neonatal

> **Descrição:** Mede a oferta de leitos neonatais em relação aos nascidos vivos.  

> **Fórmula:**  

\[
\frac{\text{Nº leitos UTI neonatal}}{\text{Nascidos vivos}} \times 1000
\]

> **Medidas:**  
> - Nº leitos UTI neonatal  
> - Nascidos vivos  

> **Unidade:**  
> - Leitos neonatais por 1.000 nascidos vivos  

> **Granularidade:**  
> - Municipal  
> - Anual  

---

# 4 Aplicação no Lakehouse

## Bronze

> Armazenamento do JSON bruto contendo:
> - Indicadores hospitalares  
> - Quantidade de leitos  
> - Dados SUS/não SUS  
> - Dados públicos/privados  
> - Informações populacionais  

---

## Silver

> Padronização e transformação dos dados:
> - Remoção do prefixo `"Numerador - "`  
> - Normalização de nomes de colunas  
> - Conversão de tipos numéricos  
> - Tratamento de valores nulos e inconsistentes  
> - Padronização dos códigos municipais  

---

## Gold

> Disponibilização de métricas analíticas prontas para:
> - Dashboards hospitalares  
> - BI em saúde pública  
> - Planejamento de infraestrutura hospitalar  
> - Modelos preditivos de demanda hospitalar  
> - Agentes de IA e consultas analíticas  