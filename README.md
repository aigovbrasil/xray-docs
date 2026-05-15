# Workflow: X-RAY-DOCS - Geração de Documentação

## Objetivo
Fornecer um motor para geração documental estruturada em escala, produzindo artefatos como MRD (Market Requirements Document), BRD (Business Requirements Document), PRD (Product Requirements Document), SOP (Standard Operating Procedures) e outros 17 artefatos padrão-ouro. Otimizar a criação e manutenção de documentação técnica e de negócios.

## ICP (Ideal Customer Profile)
Product managers, tech writers, business analysts.

## Fases do Workflow

### Fase 1: Definição do Documento (What)
*   **O Quê:** Especificação do tipo de documento a ser gerado e seu propósito.
*   **Como:** Interação com o usuário para coletar requisitos, público-alvo e informações essenciais.
*   **Output:** Brief detalhado do documento, incluindo estrutura desejada e conteúdo chave.

### Fase 2: Coleta e Estruturação de Conteúdo (How)
*   **O Quê:** Agregação e organização das informações necessárias para o documento.
*   **Como:** Utiliza skills de refatoração (`xray-docs-refactor-v1`), geração de scripts (`xray-docs-scripity-v1`) e pipelines de documentos (`xray-docs-pipeline-v1`) para coletar, formatar e estruturar o conteúdo.
*   **Output:** Rascunho estruturado do documento com seções e informações preliminares.

### Fase 3: Geração e Formatação (Where)
*   **O Quê:** Criação do documento final com formatação padrão-ouro.
*   **Como:** Aplica templates pré-definidos e regras de estilo para garantir consistência e profissionalismo. Pode gerar em múltiplos formatos (Markdown, DOCX, PDF).
*   **Output:** Documento final formatado e pronto para revisão.

### Fase 4: Revisão e Publicação (Why)
*   **O Quê:** Revisão do documento por partes interessadas e publicação.
*   **Como:** Facilita o processo de feedback e aprovação, e integra-se com sistemas de gestão de documentos ou repositórios.
*   **Output:** Documento aprovado e publicado.

## Skills Envolvidas (Exemplos)
*   `xray-docs-refactor-v1`
*   `xray-docs-scripity-v1`
*   `xray-docs-pipeline-v1`

## Pontos de Controle
*   Clareza e completude dos requisitos do documento.
*   Precisão e relevância do conteúdo.
*   Consistência da formatação e estilo.
*   Eficácia do processo de revisão e aprovação.

## Interdependências
*   Pode consumir outputs de `X-RAY-ANALYTICS` e `X-RAY-EXECUTIVE` para dados e planos.
*   Pode utilizar `X-RAY-FORGE` para incorporar diagramas ou elementos visuais nos documentos.
*   Seus documentos podem ser entregues via `X-RAY-DELIVERY`.
