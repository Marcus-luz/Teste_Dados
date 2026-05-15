# Problema Analítico: Disponibilidade de Profissionais de Saúde

## 1 Objetivo

> **Analisar** a força de trabalho em saúde vinculada ao SUS,  
> **com o propósito de** diagnosticar a densidade e a distribuição de recursos humanos em saúde,  
> **com foco em** profissionais de nível superior e técnicos por habitante,  
> **do ponto de vista de** gestores públicos e planejadores de políticas de saúde,  
> **no contexto de** dados históricos municipais do indicador RIPSA a partir de 2008.  

---

## 2 Questões

> **Q1:** Qual a densidade de enfermeiros por 1.000 habitantes nos municípios?  
> - **H1:** Existe uma disparidade significativa na oferta de enfermeiros entre diferentes municípios.  
> - **H2:** A densidade de enfermeiros cresceu proporcionalmente ao aumento da população estimada.  

> **Q2:** Qual a composição da equipe de saúde (médicos vs. técnicos) em pequenos municípios?  
> - **H1:** Municípios menores dependem mais de Agentes de Saúde e Técnicos de Enfermagem do que de médicos especialistas.  

---

## 3 Métricas

### Métrica 1 — Razão de Profissionais por 1.000 Habitantes

> **Descrição:** Calcula o número de profissionais de uma categoria específica para cada grupo de mil habitantes.  

> **Fórmula:**  

\[
\frac{\text{Numerador (Categoria)}}{\text{Denominador (População)}} \times 1000
\]

> **Medidas:**  
> - Contagem de profissionais (ex.: Enfermeiros)  
> - População estimada  

> **Unidade:**  
> - Profissionais por 1.000 habitantes  

> **Granularidade:**  
> - Municipal  
> - Anual  

---

### Métrica 2 — Índice de Diversidade de Profissionais (Skill Mix)

> **Descrição:** Verifica a variedade de categorias profissionais presentes no município.  

> **Fórmula:**  
> - Contagem de chaves `"Numerador - X"` cujo valor seja maior que 0.  

> **Medidas:**  
> - Presença de Biomédicos  
> - Fisioterapeutas  
> - Nutricionistas  
> - Outros profissionais de saúde  

> **Unidade:**  
> - Quantidade de categorias profissionais presentes  

> **Granularidade:**  
> - Municipal  

---

## 4 Aplicação no Lakehouse

### Bronze
> Armazenamento do JSON bruto original.

### Silver
> Padronização e limpeza dos dados:
> - Remoção do prefixo `"Numerador - "`  
> - Tratamento do código do município  
> - Normalização de colunas  

### Gold
> Disponibilização das métricas já calculadas para:
> - Dashboards  
> - Business Intelligence (BI)  
> - Agentes de IA  
> - Análises analíticas avançadas  