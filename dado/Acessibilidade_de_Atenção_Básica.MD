# Problema Analítico: Cobertura Territorial e Acessibilidade de Atenção Básica

## 1 Objetivo

> **Analisar** a localização e distribuição das unidades de atenção básica cadastradas no CNES,  
> **com o propósito de** diagnosticar padrões de cobertura territorial, acessibilidade e concentração espacial dos serviços de saúde,  
> **com foco em** UBS, ESF, centros de saúde e postos municipais distribuídos por bairros e municípios,  
> **do ponto de vista de** gestores do SUS, secretarias municipais de saúde e planejadores territoriais,  
> **no contexto de** dados georreferenciados do CNES contendo unidades de saúde brasileiras e suas coordenadas geográficas.  

---

# 2 Questões

> **Q1:** Como as unidades de atenção básica estão distribuídas entre bairros e municípios?  
> - **H1:** Existe concentração de UBS em regiões centrais urbanas.  
> - **H2:** Bairros periféricos possuem menor cobertura territorial de saúde.  

---

> **Q2:** Existe desigualdade regional na oferta de unidades de saúde?  
> - **H1:** Municípios maiores concentram maior número absoluto de unidades.  
> - **H2:** Municípios pequenos apresentam baixa diversidade de estabelecimentos de saúde.  

---

> **Q3:** Como a Estratégia Saúde da Família (ESF) está distribuída territorialmente?  
> - **H1:** ESFs são mais frequentes em áreas periféricas e municípios interioranos.  
> - **H2:** Grandes centros urbanos possuem maior predominância de UBS tradicionais.  

---

> **Q4:** Existem vazios assistenciais em determinadas regiões geográficas?  
> - **H1:** Áreas rurais apresentam maior distância média entre unidades de saúde.  
> - **H2:** Municípios com poucas coordenadas registradas possuem menor cobertura espacial.  

---

> **Q5:** Qual o padrão espacial entre tipos de unidades de saúde?  
> - **H1:** Centros de saúde apresentam maior centralização geográfica.  
> - **H2:** Postos e UBS possuem distribuição mais capilarizada nos bairros.  

---

# 3 Métricas

## Métrica 1 — Quantidade de Unidades por Município

> **Descrição:** Mede o total de estabelecimentos de saúde registrados em cada município.  

> **Fórmula:**  

\[
\text{Contagem de CNES agrupados por IBGE}
\]

> **Medidas:**  
> - CNES  
> - Código IBGE  

> **Unidade:**  
> - Quantidade de unidades  

> **Granularidade:**  
> - Municipal  

---

## Métrica 2 — Densidade de Unidades por Bairro

> **Descrição:** Mede a concentração de unidades de saúde em cada bairro.  

> **Fórmula:**  

\[
\text{Contagem de unidades por bairro}
\]

> **Medidas:**  
> - Bairro  
> - CNES  

> **Unidade:**  
> - Quantidade de unidades  

> **Granularidade:**  
> - Bairro  
> - Municipal  

---

## Métrica 3 — Índice de Cobertura Territorial

> **Descrição:** Mede a dispersão geográfica das unidades utilizando latitude e longitude.  

> **Fórmula:**  

\[
\text{Distância média entre unidades geográficas}
\]

> **Medidas:**  
> - Latitude  
> - Longitude  

> **Unidade:**  
> - Quilômetros (km)  

> **Granularidade:**  
> - Municipal  
> - Regional  

---

## Métrica 4 — Diversidade de Tipos de Estabelecimentos

> **Descrição:** Mede a variedade de categorias de unidades de saúde existentes no município.  

> **Fórmula:**  

\[
\text{Contagem distinta de categorias identificadas no campo NOME}
\]

> **Categorias identificáveis:**  
> - UBS  
> - ESF  
> - Centro de Saúde  
> - Unidade Básica  
> - Posto de Saúde  
> - Atendimento Domiciliar  

> **Unidade:**  
> - Quantidade de categorias  

> **Granularidade:**  
> - Municipal  

---

## Métrica 5 — Índice de Interiorização da Saúde

> **Descrição:** Mede a proporção de unidades localizadas em áreas rurais ou distritais.  

> **Fórmula:**  

\[
\frac{\text{Unidades em áreas rurais/interior}}{\text{Total de unidades}} \times 100
\]

> **Indicadores possíveis:**  
> - Bairro = Interior  
> - Distrito  
> - Área Rural  
> - Povoados  

> **Unidade:**  
> - Percentual (%)  

> **Granularidade:**  
> - Municipal  
> - Estadual  

---

## Métrica 6 — Índice de Capilaridade da Atenção Básica

> **Descrição:** Mede o espalhamento territorial das UBS e ESF em relação ao município.  

> **Fórmula:**  

\[
\frac{\text{Quantidade de UBS + ESF}}{\text{Área territorial ou população}}
\]

> **Medidas:**  
> - Quantidade de UBS  
> - Quantidade de ESF  
> - População municipal ou área territorial  

> **Unidade:**  
> - Unidades por km² ou habitantes  

> **Granularidade:**  
> - Municipal  

---

# 4 Aplicação no Lakehouse

## Bronze

> Armazenamento dos dados brutos do CNES:
> - CNES  
> - UF  
> - Código IBGE  
> - Nome da unidade  
> - Logradouro  
> - Bairro  
> - Latitude  
> - Longitude  

---

## Silver

> Padronização e enriquecimento dos dados:
> - Conversão de latitude/longitude para formato numérico  
> - Tratamento de coordenadas inválidas  
> - Padronização de bairros e logradouros  
> - Extração automática do tipo de unidade pelo campo `NOME`  
> - Normalização textual dos registros  

---

## Gold

> Disponibilização de indicadores estratégicos para:
> - Dashboards geoespaciais  
> - Mapas de cobertura territorial  
> - Planejamento de expansão da atenção básica  
> - Identificação de vazios assistenciais  
> - Sistemas de apoio à decisão em saúde pública  
> - Consultas analíticas por IA e BI  