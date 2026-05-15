# Problema Analítico: Distribuição Geográfica de Unidades de Saúde

## 1 Objetivo

> **Analisar** a distribuição espacial das unidades de saúde cadastradas no CNES,  
> **com o propósito de** diagnosticar a cobertura territorial e a concentração de estabelecimentos de saúde,  
> **com foco em** localização geográfica, distribuição municipal, cobertura urbana/rural e padrões de acesso aos serviços de atenção básica,  
> **do ponto de vista de** gestores públicos de saúde, planejadores urbanos e pesquisadores em saúde pública,  
> **no contexto de** dados georreferenciados de unidades de saúde do CNES no território brasileiro.  

---

# 2 Questões

> **Q1:** Como as unidades de saúde estão distribuídas geograficamente nos municípios brasileiros?  
> - **H1:** Existe concentração de unidades de saúde em áreas urbanas centrais.  
> - **H2:** Regiões periféricas e rurais possuem menor densidade de cobertura de saúde.  

---

> **Q2:** Qual é a relação entre quantidade de unidades e tamanho/população dos municípios?  
> - **H1:** Municípios maiores possuem maior quantidade absoluta de unidades de saúde.  
> - **H2:** Municípios pequenos apresentam menor diversidade de serviços de saúde.  

---

> **Q3:** Existem padrões regionais na distribuição das UBS e equipes de saúde da família?  
> - **H1:** A Estratégia Saúde da Família é mais presente em municípios do interior.  
> - **H2:** Capitais e grandes centros possuem maior diversidade de tipos de estabelecimentos.  

---

> **Q4:** Como a localização geográfica influencia o acesso potencial aos serviços de saúde?  
> - **H1:** Unidades localizadas em bairros centrais possuem maior proximidade entre si.  
> - **H2:** Áreas rurais apresentam maior dispersão espacial entre unidades de saúde.  

---

# 3 Métricas

## Métrica 1 — Quantidade de Unidades de Saúde por Município

> **Descrição:** Mede o número total de unidades de saúde cadastradas em cada município.  

> **Fórmula:**  

$$
\text{Contagem de CNES por município}
$$

> **Medidas:**  
> - Código CNES  
> - Código IBGE do município  

> **Unidade:**  
> - Quantidade de unidades  

> **Granularidade:**  
> - Municipal  

---

## Métrica 2 — Densidade de Unidades de Saúde

> **Descrição:** Calcula a quantidade de unidades de saúde por habitante ou área territorial.  

> **Fórmula:**  

$$
\frac{\text{Nº de unidades de saúde}}{\text{População do município}} \times 10000
$$

> **Medidas:**  
> - Quantidade de unidades CNES  
> - População municipal  

> **Unidade:**  
> - Unidades por 10.000 habitantes  

> **Granularidade:**  
> - Municipal  
> - Estadual  

---

## Métrica 3 — Índice de Cobertura Territorial

> **Descrição:** Mede a dispersão geográfica das unidades usando latitude e longitude.  

> **Fórmula:**  

$$
\text{Distância média entre unidades}
$$

> **Medidas:**  
> - Latitude  
> - Longitude  

> **Unidade:**  
> - Quilômetros (km)  

> **Granularidade:**  
> - Municipal  
> - Regional  

---

## Métrica 4 — Índice de Diversidade de Estabelecimentos

> **Descrição:** Mede a variedade de tipos de estabelecimentos de saúde existentes em cada município.  

> **Fórmula:**  

$$
\text{Contagem distinta de tipos de unidades}
$$

> **Exemplos:**  
> - UBS  
> - Centro de Saúde  
> - Estratégia Saúde da Família  
> - Postos de Saúde  
> - Atendimento Domiciliar  

> **Unidade:**  
> - Quantidade de categorias  

> **Granularidade:**  
> - Municipal  

---

## Métrica 5 — Cobertura da Atenção Básica

> **Descrição:** Mede a proporção de unidades voltadas para atenção primária em relação ao total de estabelecimentos.  

> **Fórmula:**  

$$
\frac{\text{UBS + ESF + Postos de Saúde}}{\text{Total de unidades}} \times 100
$$

> **Medidas:**  
> - Quantidade de UBS  
> - Quantidade de ESF  
> - Quantidade total de estabelecimentos  

> **Unidade:**  
> - Percentual (%)  

> **Granularidade:**  
> - Municipal  
> - Estadual  

---

# 4 Aplicação no Lakehouse

## Bronze

> Armazenamento dos dados brutos do CNES:
> - Código CNES  
> - Município (IBGE)  
> - Nome da unidade  
> - Bairro  
> - Coordenadas geográficas  
> - UF  

---

## Silver

> Padronização e enriquecimento dos dados:
> - Normalização de nomes de estabelecimentos  
> - Conversão de latitude/longitude para formato numérico  
> - Tratamento de coordenadas inválidas  
> - Padronização de bairros e municípios  
> - Classificação do tipo de unidade de saúde  

---

## Gold

> Disponibilização de indicadores analíticos para:
> - Dashboards geoespaciais  
> - Mapas de cobertura em saúde  
> - Planejamento territorial da atenção básica  
> - Identificação de vazios assistenciais  
> - Sistemas de apoio à decisão e IA analítica  
