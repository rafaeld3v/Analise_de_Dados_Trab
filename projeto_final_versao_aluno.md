# UNIFOR — Especialização em Engenharia de Dados (Turma 02)
## Projeto Final (Versão do Aluno)
## Tema: Narrativa Convincente vs Verdade Analítica

---

## 1) Desafio do Projeto

Seu objetivo é mostrar maturidade analítica em dados reais.

Cada equipe deverá construir:

1. **Narrativa Inicial** (plausível, mas frágil): uma conclusão baseada em análise inicial dos dados.
2. **Narrativa Corrigida** (robusta): uma nova conclusão após correções metodológicas, controle de vieses e testes de robustez.

O foco do projeto é provar, com evidências, como a análise correta pode mudar a decisão.

---

## 2) O que deve ser entregue

Entregáveis obrigatórios:

1. `notebook.ipynb` com o pipeline completo;
2. resumo executivo de 1 a 2 páginas (`.md` ou PDF);
3. seção explícita **Antes vs Depois**;
4. links das fontes oficiais usadas.

### Mínimos técnicos obrigatórios

- 3 gráficos no mínimo:
  - 1 temporal;
  - 1 comparativo;
  - 1 distribuição (boxplot/histograma/densidade).
- tratamento de dados ausentes e anomalias documentado;
- pelo menos 1 teste de robustez (ex.: mediana, percentis, estratificação, ponderação, taxa, ajuste temporal ou deflação).

---

## 3) Como será avaliado (resumo)

Sua nota considera:

- clareza da pergunta e da hipótese;
- qualidade da preparação dos dados;
- correção metodológica da análise;
- evidência de mudança entre “Antes” e “Depois”;
- qualidade dos gráficos e da comunicação;
- reprodutibilidade e fontes.

---

## 4) Estrutura sugerida do notebook

1. Problema e hipótese inicial  
2. Fonte e descrição dos dados  
3. Qualidade dos dados (nulos, tipos, anomalias)  
4. Narrativa Inicial  
5. Correções e testes de robustez  
6. Narrativa Corrigida  
7. Recomendação executiva  
8. Limitações do estudo

---

## 5) Escolha 1 das 10 propostas

## Proposta 01 — Combustíveis (ANP)
**Pergunta:** Qual UF é mais cara para abastecer?  
**Fonte:** [dados.gov.br](https://dados.gov.br/) (ANP preços de combustíveis)

**Ponto de atenção:** média simples pode enganar.  
**Começo sugerido:** comparar média vs mediana por UF em uma mesma janela temporal.

---

## Proposta 02 — Energia (ANEEL)
**Pergunta:** Qual distribuidora tem pior qualidade de serviço?  
**Fonte:** dados abertos ANEEL

**Ponto de atenção:** usar apenas 1 indicador e 1 período pode distorcer.  
**Começo sugerido:** analisar DEC e FEC em série temporal.

---

## Proposta 03 — Vacinação (OpenDataSUS)
**Pergunta:** A cobertura vacinal melhorou de fato?  
**Fonte:** [OpenDataSUS](https://opendatasus.saude.gov.br/)

**Ponto de atenção:** número absoluto de doses não representa cobertura real.  
**Começo sugerido:** comparar absoluto vs taxa por população-alvo.

---

## Proposta 04 — Emprego Formal (Novo CAGED)
**Pergunta:** Qual setor mais gera emprego?  
**Fonte:** Novo CAGED (MTE) / [dados.gov.br](https://dados.gov.br/)

**Ponto de atenção:** admissões sem desligamentos gera conclusão incompleta.  
**Começo sugerido:** comparar ranking por admissões vs ranking por saldo líquido.

---

## Proposta 05 — ENEM (INEP)
**Pergunta:** Qual UF tem melhor desempenho?  
**Fonte:** microdados ENEM (INEP)

**Ponto de atenção:** média geral sem estratificação pode induzir erro.  
**Começo sugerido:** comparar resultados por rede (pública/privada).

---

## Proposta 06 — Trânsito (PRF + IBGE)
**Pergunta:** Onde é mais perigoso no trânsito?  
**Fonte:** PRF + IBGE

**Ponto de atenção:** total de acidentes sem taxa de exposição pode enganar.  
**Começo sugerido:** comparar número absoluto vs taxa por 100 mil habitantes/frota.

---

## Proposta 07 — Queimadas (INPE)
**Pergunta:** Qual estado mais piorou em queimadas?  
**Fonte:** [INPE Queimadas](https://terrabrasilis.dpi.inpe.br/queimadas/)

**Ponto de atenção:** totais anuais sem contexto de área/sazonalidade.  
**Começo sugerido:** comparar absoluto vs taxa por área e mês equivalente.

---

## Proposta 08 — Empresas Listadas (CVM)
**Pergunta:** Qual empresa está mais saudável financeiramente?  
**Fonte:** [dados.cvm.gov.br](https://dados.cvm.gov.br/)

**Ponto de atenção:** lucro isolado não representa saúde financeira completa.  
**Começo sugerido:** combinar lucro, margem e endividamento entre empresas do mesmo setor.

---

## Proposta 09 — Clima (INMET)
**Pergunta:** Qual cidade é mais quente?  
**Fonte:** [INMET](https://portal.inmet.gov.br/)

**Ponto de atenção:** período curto pode distorcer resultado.  
**Começo sugerido:** comparar mediana e extremos (p95/p99) em 12 meses.

---

## Proposta 10 — Orçamento Público
**Pergunta:** Qual área é mais priorizada no orçamento?  
**Fonte:** [Portal da Transparência](https://portaldatransparencia.gov.br/)

**Ponto de atenção:** autorizado não é igual a executado.  
**Começo sugerido:** comparar autorizado vs pago (idealmente em valores reais).

---

## 6) Checklist final antes da entrega

- [ ] Pergunta clara e hipótese inicial explícita  
- [ ] Fonte oficial citada com link  
- [ ] Qualidade de dados analisada (nulos/anomalias)  
- [ ] Narrativa Inicial construída  
- [ ] Análise corrigida com método robusto  
- [ ] Comparação Antes vs Depois objetiva  
- [ ] Recomendação executiva final  
- [ ] Limitações do estudo declaradas

---

## 7) Estrutura do pitch (3 minutos)

1. Problema e hipótese inicial (30s)  
2. Narrativa Inicial (45s)  
3. Correções metodológicas (45s)  
4. Narrativa Corrigida (45s)  
5. Recomendação final (15s)

---

## 8) Boas práticas

- Não force a conclusão: deixe os dados “falarem”.
- Explique toda decisão de limpeza/transformação.
- Prefira comparações justas (mesmo período, mesma base de referência).
- Sempre indique limitações e riscos residuais.

