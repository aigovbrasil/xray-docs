# Padrão de refatoração documental

Este arquivo é a fonte operacional de verdade para classificação, naming e materialização.

## Objetivo do skill
Transformar documentos brutos em artefatos operacionais organizados por fase do negócio, com nomes consistentes, metadata de rastreabilidade e um pacote zip final. Também suporta geração de novos documentos a partir de contexto fornecido pelo usuário.

## Fases válidas (`phase_key`)
- `00_admin`
- `01_estrategia`
- `02_discovery_validacao`
- `03_mvp_produto`
- `04_vendas_marketing`
- `05_operacao_entrega`
- `06_financeiro_legal`
- `07_growth_analytics`
- `99_arquivo`

## Mapeamento de pasta (`phase_key` → pasta)
- `00_admin` → `00_admin`
- `01_estrategia` → `01_estrategia`
- `02_discovery_validacao` → `02_discovery-validacao`
- `03_mvp_produto` → `03_mvp-produto`
- `04_vendas_marketing` → `04_vendas-marketing`
- `05_operacao_entrega` → `05_operacao-entrega`
- `06_financeiro_legal` → `06_financeiro-legal`
- `07_growth_analytics` → `07_growth-analytics`
- `99_arquivo` → `99_arquivo`

## Tipos documentais válidos (`doc_type`) — completo

### Estratégia e validação
- `mrd` → `01_estrategia` — Market Requirements Document
- `brd` → `01_estrategia` — Business Requirements Document
- `prfaq` → `02_discovery_validacao` — Press Release + FAQ
- `lean-canvas` → `01_estrategia`
- `hipoteses-criticas` → `01_estrategia`
- `icp-card` → `01_estrategia`
- `metricas-norte` → `01_estrategia`

### Discovery e validação
- `roteiro-entrevista` → `02_discovery_validacao`
- `log-entrevistas` → `02_discovery_validacao`
- `experimentos` → `02_discovery_validacao`
- `oferta-onepager` → `02_discovery_validacao`
- `pipeline-validacao` → `02_discovery_validacao`

### Produto e engenharia
- `prd` → `03_mvp_produto` — Product Requirements Document (completo)
- `prd-lite` → `03_mvp_produto` — PRD simplificado para solo founder
- `frd` → `03_mvp_produto` — Functional Requirements Document
- `nfr` → `03_mvp_produto` — Non-Functional Requirements
- `backlog-mvp` → `03_mvp_produto`
- `user-stories` → `03_mvp_produto`
- `fluxos-ux` → `03_mvp_produto`
- `dicionario-de-dados` → `03_mvp_produto`

### Crescimento e direção
- `roadmap` → `07_growth_analytics` — Roadmap Now/Next/Later
- `roadmap-now-next-later` → `07_growth_analytics`
- `experimentos-growth` → `07_growth_analytics`
- `dashboard-negocio` → `07_growth_analytics`

### Vendas e marketing
- `mensagem-comercial-base` → `04_vendas_marketing`
- `faq-objecoes` → `04_vendas_marketing`
- `crm-comercial` → `04_vendas_marketing`
- `dashboard-comercial` → `04_vendas_marketing`

### Operação e entrega
- `sop` → `05_operacao_entrega` — SOP genérico
- `sop-onboarding` → `05_operacao_entrega`
- `sop-entrega` → `05_operacao_entrega`
- `sop-suporte` → `05_operacao_entrega`
- `runbook` → `05_operacao_entrega` — Rotina técnica ou resposta a incidente
- `operacoes-semana` → `05_operacao_entrega`
- `change-log` → `05_operacao_entrega`

### Financeiro e legal
- `fluxo-caixa` → `06_financeiro_legal`
- `dre-gerencial` → `06_financeiro_legal`
- `precificacao` → `06_financeiro_legal`

### Administração
- `readme-operacional` → `00_admin`
- `indice-mestre` → `00_admin`
- `stack-acessos` → `00_admin`

### Fallback
- `outro` → `99_arquivo`

## Extensões alvo por doc_type
- padrão: `.md`
- `.json` para: `stack-acessos`, `log-entrevistas`, `experimentos`, `pipeline-validacao`, `backlog-mvp`, `user-stories`, `dicionario-de-dados`, `crm-comercial`, `dashboard-comercial`, `operacoes-semana`, `fluxo-caixa`, `dre-gerencial`, `precificacao`, `experimentos-growth`, `dashboard-negocio`
- `.docx` apenas quando o formato de documento é claramente superior ao markdown

## Regras de naming
Formato-base: `AA_doc-type_YYYY-MM_titulo-curto_v01.ext`

- `AA` = prefixo numérico da fase (`00`, `01`, `02`, ...)
- `doc-type` = slug do tipo documental
- `YYYY-MM` = data de geração
- `titulo-curto` = slug curto do título
- `v01` = versão inicial

**Colisão de nomes:** se o arquivo já existe, o script incrementa automaticamente a versão (`v02`, `v03` ...).

### Restrições
- letras minúsculas, números, hífen e underscore
- sem acentos, espaços ou símbolos
- nome-base: 25–48 caracteres antes da extensão
- caminho completo ≤ 180 caracteres
- proibido: `final`, `novo`, `ok`, `versao boa`, `teste`

## Packs lógicos (ver `config/default.json → packs`)
- `solo-mvp` — PRFAQ + PRD-lite + User Stories + NFR + SOP
- `stakeholder` — MRD + BRD + PRD + Roadmap
- `tecnico` — FRD + NFR + Runbook + User Stories
- `operacional` — SOP (variantes) + Runbook
- `completo` — todos os novos tipos habilitados

## Templates de conteúdo
Consulte `references/doc-templates.md` para a estrutura de cada tipo documental novo (MRD, BRD, PRFAQ, PRD, FRD, NFR, Roadmap, User Stories, SOP, Runbook).

## Campos obrigatórios do `work_order.json`
Cada item de `documents` deve conter:
- `source_path` (vazio `""` se o doc está sendo gerado do zero)
- `detected_ext`
- `phase_key`
- `doc_type`
- `title`
- `objective`
- `target_extension`
- `refactored_content`
- `warnings`
- `confidence`

## Regras semânticas
- Preserve o significado original
- Remova redundância, ruído e ambiguidade
- Prefira títulos curtos e funcionais
- Marque `INCOMPLETO` onde faltar contexto crítico
- Se `confidence < 0.60`, registre warning pedindo revisão manual
- Se um arquivo misturar temas, priorize o dominante e registre em `warnings`

## Resultado esperado
Ao final, a pasta de saída deve conter: árvore por fase, documentos refatorados, `*.meta.json` por documento, `manifest.json`, `report.json`, `output_refatorado.zip`.
