# Resumo Executivo — Cobertura Vacinal de Poliomielite Injetável (VIP) no Brasil

**Projeto Final · Especialização em Engenharia de Dados — UNIFOR · Turma 02**  
**Tema:** Vacinação · Painel SEIDIGI/DEMAS — Ministério da Saúde  
**Equipe:** Dante Dantas - 2518583, Rafael Tavares - 2517595 · **Prof. Cassio Pinheiro · Abril/2026**

---

## A pergunta

A cobertura vacinal contra poliomielite injetável (VIP) no Brasil está em níveis adequados?

## A resposta curta

**Não. O Brasil está estruturalmente abaixo da meta de 95% — em 38 meses observados (jan/2023 a fev/2026), apenas 5 atingiram a meta, e os 5 são todos janeiros, com cobertura artificialmente inflada por ajustes administrativos.** Quem olha apenas a média anual pode concluir, erradamente, que o programa está adequado.

---

## Por que a métrica importa

|                             | **Narrativa Inicial** (frágil) | **Narrativa Corrigida** (robusta) |
| --------------------------- | ------------------------------ | --------------------------------- |
| **Métrica**                 | Média anual de cobertura       | % de meses na meta + série mensal |
| **Granularidade**           | Anual                          | Mensal                            |
| **Tratamento de outliers**  | Nenhum                         | Janeiros marcados como artefatos  |
| **Cobertura 2023**          | 84,5 % (média)                 | 92 % dos meses < meta             |
| **Cobertura 2024**          | 92,5 % (média)                 | 83 % dos meses < meta             |
| **Cobertura 2025**          | 86,9 % (média)                 | 92 % dos meses < meta             |
| **Tendência aparente**      | "subiu, depois caiu"           | Estagnação                        |
| **Meses na meta (38 obs)**  |                                | **5 — todos janeiros**            |
| **Sem outliers de janeiro** |                                | **97 % dos meses < meta**         |

A "melhora" aparente de 2024 (92,5%) foi puxada por um **único mês excepcional** (jan/2024 com 111,8% — registro administrativo, não cobertura real). Em 2025 a média voltou ao patamar de 2023, confirmando que não há tendência sustentada.

---

## Como a análise foi corrigida

1. **Substituímos média anual por análise mensal**, com a linha da meta de 95% sempre visível.
2. **Marcamos os outliers de janeiro** (5 observações com cobertura >100%, todas em janeiro de cada ano). Não removidos — o tratamento explícito é parte da análise.
3. **Decompusemos o perfil sazonal** — a cobertura cai sistematicamente entre maio e julho, com mediana ~80% nesses meses.
4. **Adotamos a métrica direta de fracasso** — % de meses abaixo da meta, em cada ano, sem ambiguidades.

---

## Implicações práticas

1. **Revisar a comunicação oficial.** Apresentar "média anual de cobertura" não é métrica adequada — esconde o fato de que a meta é raramente atingida em meses individuais. A métrica oficial deve ser **% de meses na meta** + **mediana mensal**.

2. **Reconhecer o risco epidemiológico real.** Cobertura mediana de 87% é insuficiente para imunidade de rebanho contra poliovírus, que exige ≥95%. O Brasil está em **risco real** de reintrodução da pólio.

3. **Mover a campanha de intensificação.** O perfil sazonal mostra que o vale de cobertura é entre **maio e julho**, não dezembro/janeiro. As ações de mobilização tradicionalmente concentradas no fim do ano deveriam ser antecipadas para o meio do ano.

4. **Auditar o registro de janeiro.** Os picos >100% indicam doses sendo registradas fora do mês de aplicação (atraso de digitação, ajustes retroativos, correção de denominador IBGE). Corrigir isso melhora a qualidade de toda a série histórica do SI-PNI.

---

## Limitações declaradas

- Análise restrita à **vacina VIP** (poliomielite injetável); outras vacinas do calendário podem ter padrões distintos.
- Granularidade **nacional** — heterogeneidade regional (Norte/Nordeste vs Sul/Sudeste) ficou fora do escopo.
- Janela de **38 meses** (jan/2023 a fev/2026); não permite comparação com período pré-pandemia.
- Dados de **fev/2026 são parciais** — o ano ainda está em curso.
- Cobertura registrada ≠ cobertura real (subnotificação no setor privado).
- Outliers de janeiro **mantidos e marcados**, não removidos — exige que o leitor entenda que são artefatos.

---

## Fonte e reprodução

**Painel:** Cobertura Vacinal do Calendário Nacional de Vacinação por Local de Residência  
**Mantenedor:** Ministério da Saúde — SEIDIGI / DEMAS  
**URL:** https://infoms.saude.gov.br/extensions/SEIDIGI_DEMAS_VACINACAO_CALENDARIO_NACIONAL_COBERTURA_RESIDENCIA/SEIDIGI_DEMAS_VACINACAO_CALENDARIO_NACIONAL_COBERTURA_RESIDENCIA.html  
**Filtros aplicados:** Imunobiológico = "Polio Injetável (VIP)"; granularidade mensal; escopo Brasil.

**Notebook reprodutível:** `projeto_final_vacinacao.ipynb` — documenta cada filtro, decisão metodológica e teste de robustez, com gráficos temporais, comparativos (heatmap mês×ano) e de distribuição (boxplot por ano + perfil sazonal).
