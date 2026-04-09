# CONTEXT.md — Landing Page de Portfólio | Data Engineering

## Visão Geral

Landing page pessoal e profissional de **Felipe Piva**, Data Engineer na CNH Industrial (Curitiba, Brasil). O objetivo é funcionar como um portfólio técnico moderno que demonstre competências em engenharia de dados, projetos relevantes e stack tecnológica — posicionando o perfil para oportunidades de nível Pleno/Sênior no mercado brasileiro e internacional.

---

## Público-Alvo

| Persona | O que procura |
|---|---|
| **Recrutadores técnicos** | Stack, experiência, senioridade, certificações |
| **Tech Leads / Hiring Managers** | Profundidade técnica, arquitetura de soluções, capacidade de decisão |
| **Comunidade / Peers** | Projetos open-source, contribuições, artigos |
| **Clientes PJ** | Escopo de serviço, cases de sucesso, contato rápido |

---

## Seções da Página

### 1. Hero
- Nome, título (Data Engineer), tagline curta e impactante
- CTA principal: "Ver Projetos" / "Fale Comigo"
- Animação sutil de entrada (staggered reveal)
- Indicador visual de scroll

### 2. Sobre / Bio
- Resumo profissional conciso (3-4 linhas)
- Empresa atual (CNH Industrial), formação (B.Sc. Data Science — FAE)
- Certificações: AZ-900 (em preparação), NVIDIA DLI
- Localização: Curitiba, PR, Brasil

### 3. Stack Tecnológica
- Apresentação visual (ícones/badges agrupados por categoria):
  - **Core**: PySpark, Databricks, Delta Lake, Unity Catalog
  - **Cloud**: Azure (ADLS Gen2, ADF, Event Hubs), Terraform
  - **Orquestração**: Airflow, DLT (Databricks Live Tables)
  - **Analytics**: Power BI, DAX, SQL
  - **Linguagens**: Python, SQL, Scala (em aprendizado)
  - **DevOps**: Git, Azure DevOps, GitHub Actions, CI/CD
  - **Outros**: SharePoint/Graph API, Kafka, dbt, Docker

### 4. Projetos em Destaque
Cards interativos com:
- Título do projeto
- Descrição curta (2 linhas)
- Tags de tecnologias usadas
- Link para GitHub / demo / case study
- Indicador visual de complexidade ou tipo (batch, streaming, lakehouse)

**Projetos sugeridos:**
| Projeto | Tipo | Stack Principal |
|---|---|---|
| Pipeline HLIB — Time Reduction | Produção (CNH) | PySpark, Delta Lake, Medallion, Power BI |
| Carga Máquina M13 | Produção (CNH) | PySpark, Star Schema, Power BI |
| NASA Lakehouse | Portfólio | Databricks, Delta Lake, Unity Catalog |
| IoT OEE Streaming | Portfólio | Kafka, Spark Streaming, Delta Lake |
| Open-Source Lakehouse | Portfólio / OSS | Unity Catalog OSS, Iceberg, MinIO, Trino |
| E-commerce DLT Pipeline | Portfólio | DLT, Auto Loader, Terraform, CI/CD |
| Pipeline Ações BR | Portfólio | Azure (ADLS, ADF, Event Hubs), Databricks |

### 5. Experiência / Timeline
- Timeline vertical ou horizontal minimalista
- Marcos: Estágio CNH → Data Engineer CNH → Projetos-chave → Certificações
- Datas e descrições curtas

### 6. Contato / CTA Final
- Links: GitHub (FelipePiva03), LinkedIn, Email
- Formulário simples ou CTA direto (mailto / link externo)
- Frase de fechamento motivacional

---

## Requisitos Técnicos

- **Framework**: HTML + CSS + JS (single-page, sem framework pesado) OU React (JSX artifact)
- **Responsivo**: Mobile-first, breakpoints em 768px e 1200px
- **Performance**: Lazy loading de imagens, CSS animations (sem libs pesadas)
- **Acessibilidade**: Semântica HTML5, contraste WCAG AA, navegação por teclado
- **SEO**: Meta tags, Open Graph, structured data básico
- **Dark mode**: Tema principal escuro (afinidade com Gruvbox/terminal aesthetic)

---

## Tom de Voz

- Profissional mas não corporativo
- Direto e objetivo (reflete o estilo pessoal)
- Confiante sem ser arrogante
- Técnico quando necessário, acessível quando possível
- Bilingue: conteúdo principal em inglês (alcance internacional), com toggle opcional para PT-BR

---

## Referências de Estilo

- Portfólios de engenheiros de dados / ML engineers no Dribbble e Awwwards
- Estética de terminais modernos (Warp, Hyper)
- Dashboards de observabilidade (Grafana, Datadog) como inspiração para data viz
- Design editorial tech (Stripe, Vercel, Linear)

---

## Métricas de Sucesso

- Visitante entende o perfil técnico em < 10 segundos
- Navegação completa da página em < 2 minutos
- CTA de contato acessível em qualquer ponto da página
- Projetos demonstram range (batch, streaming, lakehouse, BI, infra)
