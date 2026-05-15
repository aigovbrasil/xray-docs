# Templates dos tipos documentais

Este arquivo contém os templates de conteúdo para cada tipo documental expandido.
Use estes templates como estrutura base do `refactored_content` de cada documento.
Para versão **lite**, respeite o `max_chars` e os `required_sections` definidos em `config/default.json`.

---

## MRD — Market Requirements Document

```markdown
# MRD: {titulo}

## Mercado-alvo
Segmento principal: [descrever quem são, tamanho estimado, contexto]
Perfil do comprador: [quem decide a compra]
Perfil do usuário: [quem usa no dia a dia]

## Dores principais
- [Dor 1 — frequência e impacto]
- [Dor 2]
- [Dor 3]

## Oportunidade
[Por que agora? O que mudou no mercado, na tecnologia ou no comportamento que abre espaço?]

## Contexto competitivo
| Alternativa atual | Limitação principal |
|---|---|
| [Alternativa A] | [Limitação] |
| [Alternativa B] | [Limitação] |

## Critérios de sucesso de mercado
- [Métrica 1: ex. 50 clientes pagantes em 90 dias]
- [Métrica 2]

## Referências e fontes
- [Entrevistas, dados, artigos que embasam]
```

**Fase:** `01_estrategia` | **Extensão:** `.md` | **Quando usar:** antes de decidir o que construir.

---

## BRD — Business Requirements Document

```markdown
# BRD: {titulo}

## Objetivo de negócio
[O que o projeto precisa entregar do ponto de vista empresarial? Qual resultado ou mudança de estado?]

## Escopo
**Inclui:**
- [Item 1]
- [Item 2]

**Não inclui (out of scope):**
- [Item 1]

## Stakeholders
| Nome / Papel | Interesse / Responsabilidade |
|---|---|
| [Stakeholder A] | [decisor final / revisor / executor] |

## Requisitos de negócio
- RN01: [Requisito — ex. O sistema deve suportar múltiplos CNPJs]
- RN02: [Requisito]

## Restrições e premissas
- [Orçamento, prazo, compliance, dependências]

## Critérios de aceitação do negócio
- [Condição objetiva que indica sucesso do projeto]

## Riscos principais
| Risco | Probabilidade | Impacto | Mitigação |
|---|---|---|---|
| [Risco 1] | Alta/Média/Baixa | Alto/Médio/Baixo | [Ação] |
```

**Fase:** `01_estrategia` | **Extensão:** `.md` ou `.docx` | **Quando usar:** múltiplos decisores, escopo contratual ou orçamento envolvido.

---

## PRFAQ — Press Release + FAQ

```markdown
# PRFAQ: {titulo}

---

## Press Release

**[Cidade, Data]** — [Nome do produto/empresa] lança [nome da solução], uma [categoria curta] que permite [benefício principal] para [público-alvo].

### O problema
[1–2 frases descrevendo a dor real do cliente hoje.]

### A solução
[2–3 frases descrevendo o que o produto faz e por que é diferente.]

### Citação do fundador
> "[Frase que comunica a visão e o porquê.]" — [Nome], fundador

### Citação do cliente (hipotética)
> "[Frase que um cliente ideal diria se já usasse o produto.]" — [Persona]

### Como começar
[URL ou call to action]

---

## FAQ — Perguntas frequentes

**Para o cliente:**

1. **[Pergunta sobre o problema ou dor]**
   [Resposta curta e direta.]

2. **[Pergunta sobre o produto]**
   [Resposta.]

3. **[Pergunta sobre confiança/segurança]**
   [Resposta.]

4. **[Pergunta sobre preço ou modelo de negócio]**
   [Resposta.]

5. **[Objeção principal esperada]**
   [Resposta.]

**Interno (negócio):**

6. **Por que agora?**
   [Resposta.]

7. **Qual o risco maior?**
   [Resposta.]

8. **Como medimos sucesso nos primeiros 90 dias?**
   [Resposta.]
```

**Fase:** `02_discovery_validacao` | **Extensão:** `.md` | **Quando usar:** ideia ainda nebulosa, validar proposta comercialmente.

---

## PRD — Product Requirements Document

```markdown
# PRD: {titulo}

## Objetivo
[Em 2–3 frases: qual problema o produto resolve, para quem e como medimos sucesso.]

## Contexto
[Decisão já tomada de construir. O que levou a isso? MRD/PRFAQ de referência se existir.]

## Usuários-alvo
| Persona | Dor principal | Métrica de sucesso |
|---|---|---|
| [Persona A] | [Dor] | [Métrica] |

## Funcionalidades

### P0 — Obrigatórias para lançamento
- [ ] [Funcionalidade 1 — descrição curta e objetivo]
- [ ] [Funcionalidade 2]

### P1 — Importantes, mas não bloqueantes
- [ ] [Funcionalidade 3]

### P2 — Futuras
- [ ] [Funcionalidade 4]

## Fora do escopo
- [O que explicitamente não será construído nesta versão]

## Critérios de sucesso
- [Métrica 1 + meta + prazo]
- [Métrica 2]

## Dependências e riscos
- [Integrações externas, decisões pendentes, riscos técnicos]

## Open questions
- [ ] [Decisão ou incógnita ainda em aberto]
```

**Fase:** `03_mvp_produto` | **Extensão:** `.md` ou `.docx` | **Quando usar:** decisão de construir tomada, alinhar design, dev e negócio.

---

## FRD — Functional Requirements Document

```markdown
# FRD: {titulo}

## Objetivo
[Detalhar o que o sistema deve fazer — comportamento operacional preciso.]

## Escopo funcional
[Quais módulos/fluxos este FRD cobre]

## Fluxos principais

### Fluxo 1: {nome do fluxo}
**Gatilho:** [O que inicia o fluxo]
**Ator:** [Usuário / sistema / integração]

| Passo | Ação | Resultado esperado |
|---|---|---|
| 1 | [Ação do ator] | [Resposta do sistema] |
| 2 | [Ação] | [Resultado] |

**Exceções:**
- [Cenário de erro 1 → comportamento esperado]

### Fluxo 2: {nome}
[Repetir estrutura acima]

## Regras de negócio
- RN01: [Regra — ex. Campo CPF deve ser validado via Receita Federal]
- RN02: [Regra]

## Validações e campos
| Campo | Tipo | Obrigatório | Regra de validação |
|---|---|---|---|
| [Campo] | texto/número/data | Sim/Não | [Regra] |

## Integrações
| Sistema externo | Tipo | Dados trafegados | Comportamento em falha |
|---|---|---|---|
| [API X] | REST/webhook | [dados] | [fallback] |

## INCOMPLETO
[Registrar aqui qualquer decisão ou comportamento ainda indefinido]
```

**Fase:** `03_mvp_produto` | **Extensão:** `.md` | **Quando usar:** automação relevante, regras de negócio complexas, desenvolvimento terceirizado.

---

## NFR — Non-Functional Requirements

```markdown
# NFR: {titulo}

## Performance
- NFR01: Tempo de resposta de [endpoint/ação] deve ser ≤ [X ms] para [Y% das requisições]
- NFR02: [Outro requisito de performance]

## Disponibilidade
- NFR03: Uptime mínimo de [X%] mensais ([Y horas de downtime tolerado/mês])
- NFR04: [Janela de manutenção aceitável]

## Segurança
- NFR05: Autenticação obrigatória via [método — ex. OAuth2/MFA]
- NFR06: Dados em trânsito criptografados via TLS 1.2+
- NFR07: [Controle de acesso / RBAC / logs de auditoria]

## Privacidade e compliance
- NFR08: Dados pessoais tratados conforme LGPD — [base legal aplicável]
- NFR09: Retenção de dados: [X dias/anos] para [tipo de dado]
- NFR10: Direito de exclusão: [como será implementado]

## Escalabilidade e capacidade
- NFR11: Suportar [X usuários simultâneos / Y requisições/segundo] sem degradação
- NFR12: [Limite de armazenamento / crescimento esperado]

## Usabilidade
- NFR13: Tempo de onboarding do novo usuário ≤ [X minutos] sem suporte
- NFR14: [Acessibilidade — WCAG nível A/AA se aplicável]

## Monitoramento e observabilidade
- NFR15: Alertas automáticos para [erros > X% / latência > Y ms]
- NFR16: Logs retidos por [X dias] com possibilidade de busca

## Notas e contexto
[Justificativas para os requisitos acima, referências a SLAs ou contratos]
```

**Fase:** `03_mvp_produto` | **Extensão:** `.md` | **Quando usar:** sempre que houver risco técnico, LGPD, SLA ou expectativa de performance.

---

## Roadmap

```markdown
# Roadmap: {titulo}

## Visão
[Em 1–2 frases: onde queremos chegar e em quanto tempo]

## Princípios de priorização
- [Princípio 1 — ex. Priorizar retenção antes de aquisição]
- [Princípio 2]

## Now — próximos 30–60 dias
| Iniciativa | Objetivo | Responsável | Status |
|---|---|---|---|
| [Iniciativa A] | [Resultado esperado] | [Pessoa/time] | Em andamento / Planejado |

## Next — 60–120 dias
| Iniciativa | Objetivo | Dependência |
|---|---|---|
| [Iniciativa B] | [Resultado] | [O que precisa estar pronto antes] |

## Later — 120+ dias
| Iniciativa | Hipótese | Gatilho para entrar em Next |
|---|---|---|
| [Iniciativa C] | [Por que achamos que vale] | [Condição] |

## O que não estamos fazendo agora (e por quê)
- [Item fora do roadmap + razão]

## Última atualização
[Data] — [O que mudou]
```

**Fase:** `07_growth_analytics` | **Extensão:** `.md` | **Quando usar:** alinhamento estratégico de direção e prioridades.

---

## User Stories / Backlog

```json
{
  "epics": [
    {
      "id": "EP01",
      "titulo": "Nome do épico",
      "objetivo": "Resultado de negócio que este épico entrega",
      "stories": [
        {
          "id": "US01",
          "como": "persona ou papel",
          "quero": "ação ou funcionalidade",
          "para": "benefício ou objetivo",
          "criterios_aceite": [
            "Dado [contexto], quando [ação], então [resultado esperado]",
            "Dado [contexto], quando [ação], então [resultado]"
          ],
          "prioridade": "P0/P1/P2",
          "estimativa": "P/M/G",
          "status": "backlog/em-desenvolvimento/pronto"
        }
      ]
    }
  ]
}
```

**Fase:** `03_mvp_produto` | **Extensão:** `.json` | **Quando usar:** transformar PRD/FRD em trabalho executável.

---

## SOP — Standard Operating Procedure

```markdown
# SOP: {titulo}

## Objetivo
[O que este procedimento garante / qual problema resolve]

## Escopo
**Quando usar:** [Situação que dispara este SOP]
**Quando não usar:** [Exceções ou situações similares que têm SOP próprio]

## Responsável
- **Executor:** [Quem executa]
- **Revisor:** [Quem valida ou aprova]
- **Frequência:** [Diário / semanal / por demanda / acionado por evento]

## Pré-requisitos
- [ ] [Acesso ou recurso necessário antes de iniciar]
- [ ] [Informação que precisa estar disponível]

## Passos

### 1. {Nome da etapa}
[Descrição clara do que fazer. Seja específico — evite "verifique se está correto".]

**Resultado esperado:** [Como saber que a etapa foi concluída corretamente]

### 2. {Nome da etapa}
[Descrição]

**Resultado esperado:** [...]

### 3. {Nome da etapa}
[...]

## Exceções e erros comuns
| Situação | O que fazer |
|---|---|
| [Erro ou exceção comum] | [Ação corretiva] |
| [Situação ambígua] | [Decisão padrão] |

## Checklist final
- [ ] [Verificação 1]
- [ ] [Verificação 2]

## Histórico de revisões
| Versão | Data | Mudança |
|---|---|---|
| v01 | [data] | Criação |
```

**Fase:** `05_operacao_entrega` | **Extensão:** `.md` | **Quando usar:** tarefas repetitivas que precisam de consistência.

---

## Runbook

```markdown
# Runbook: {titulo}

## Tipo
[ ] Rotina recorrente  [ ] Resposta a incidente  [ ] Manutenção programada

## Gatilho
[O que aciona este runbook — alerta, horário, evento manual, falha de sistema]

## Severidade / Impacto
[ ] P1 — Crítico (sistema fora do ar)
[ ] P2 — Degradado (funcionalidade parcial)
[ ] P3 — Baixo impacto

## Diagnóstico rápido

### Verificações iniciais
```bash
# [Comando ou ação de diagnóstico 1]
# [Comando ou ação 2]
```

| Sintoma | Causa provável |
|---|---|
| [Sintoma 1] | [Causa] |
| [Sintoma 2] | [Causa] |

## Ações

### Cenário A: {nome do cenário}
1. [Passo 1]
2. [Passo 2]
3. Verificar: [como confirmar que resolveu]

### Cenário B: {nome}
1. [...]

## Rollback
[Como desfazer a ação se algo der errado]

## Escalonamento
| Condição | Próximo passo | Contato |
|---|---|---|
| [Não resolveu em X min] | [Ação] | [Pessoa/canal] |

## Pós-incidente
- [ ] Registrar no change-log
- [ ] Atualizar este runbook se necessário
- [ ] Comunicar stakeholders se impacto > [threshold]

## Última execução
[Data] — [Resultado] — [Executado por]
```

**Fase:** `05_operacao_entrega` | **Extensão:** `.md` | **Quando usar:** stack técnica com automações, integrações ou alertas.
