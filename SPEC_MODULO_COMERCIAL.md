# ESPECIFICACAO: MODULO COMERCIAL
## Hub WFinance | Pipeline de Vendas

**Versao:** 1.0
**Data:** 13/01/2026
**Status:** Especificacao para desenvolvimento

---

## 1. VISAO GERAL

### Objetivo
Criar um modulo comercial completo dentro do Hub WFinance para gerenciar todo o processo de vendas, desde a captacao ate o fechamento, com automacoes de nutricao e acompanhamento.

### Funcionalidades Principais
```
┌─────────────────────────────────────────────────────────────────────────┐
│                      MODULO COMERCIAL - VISAO GERAL                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                    DASHBOARD PRINCIPAL                          │   │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐          │   │
│  │  │ Metricas │ │ Tarefas  │ │ Pipeline │ │ Nutricao │          │   │
│  │  │   Hoje   │ │   Hoje   │ │  Visual  │ │  Status  │          │   │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘          │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                    PIPELINE KANBAN                              │   │
│  │                                                                 │   │
│  │  Captacao │ Aquecimento │ Contato │ Qualificado │ Proposta    │   │
│  │    [3]    │     [5]     │   [2]   │     [1]     │    [1]      │   │
│  │           │             │         │             │              │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                    PAINEL LATERAL                               │   │
│  │  - Detalhes do Lead                                             │   │
│  │  - Historico de Interacoes                                      │   │
│  │  - Acoes Rapidas                                                │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 2. ESTRUTURA DE DADOS

### 2.1 Tabela: Leads (Azure Table Storage)

**PartitionKey:** `lead`
**RowKey:** `{cnpj}` ou `{uuid}`

| Campo | Tipo | Descricao | Exemplo |
|-------|------|-----------|---------|
| id | string | Identificador unico | "uuid-123" |
| cnpj | string | CNPJ da empresa | "12.345.678/0001-90" |
| nomeFantasia | string | Nome da otica | "Otica Cristal" |
| razaoSocial | string | Razao social | "Cristal Otica Ltda" |
| telefoneComercial | string | Telefone da empresa | "(82) 3333-4444" |
| emailComercial | string | Email da empresa | "contato@oticacristal.com" |
| instagram | string | @ do Instagram | "@oticacristal" |
| endereco | string | Endereco completo | "Rua X, 123 - Maceio/AL" |
| ratingGoogle | number | Avaliacao Google | 4.7 |
| score | number | Score de qualificacao | 92 |
| tier | string | Classificacao | "T1" |
| fonte | string | Origem do lead | "discovery" |
| dataCriacao | datetime | Quando foi captado | "2026-01-10T10:00:00Z" |

### 2.2 Tabela: Decisores

**PartitionKey:** `decisor`
**RowKey:** `{lead_id}_{decisor_id}`

| Campo | Tipo | Descricao | Exemplo |
|-------|------|-----------|---------|
| id | string | Identificador unico | "uuid-456" |
| leadId | string | FK para Lead | "uuid-123" |
| nome | string | Nome completo | "Joao Silva" |
| cargo | string | Cargo na empresa | "Proprietario" |
| whatsapp | string | WhatsApp pessoal | "(82) 99999-8888" |
| email | string | Email pessoal | "joao@gmail.com" |
| instagramPessoal | string | Instagram pessoal | "@joaosilva" |
| principal | boolean | E o decisor principal? | true |

### 2.3 Tabela: Deals (Negocios)

**PartitionKey:** `deal`
**RowKey:** `{deal_id}`

| Campo | Tipo | Descricao | Exemplo |
|-------|------|-----------|---------|
| id | string | Identificador unico | "uuid-789" |
| leadId | string | FK para Lead | "uuid-123" |
| status | string | Etapa do pipeline | "aquecimento" |
| dataStatus | datetime | Quando mudou de status | "2026-01-12T14:00:00Z" |
| proximaAcao | string | Proxima acao pendente | "enviar_dm" |
| dataProximaAcao | datetime | Quando executar | "2026-01-15T09:00:00Z" |
| pacote | string | Pacote de interesse | "Growth" |
| valorEstimado | number | Valor da proposta | 1197 |
| motivoPerda | string | Se perdido, por que | null |
| dataCriacao | datetime | Inicio da negociacao | "2026-01-10T10:00:00Z" |
| dataFechamento | datetime | Quando fechou/perdeu | null |

### 2.4 Tabela: Historico de Interacoes

**PartitionKey:** `historico`
**RowKey:** `{deal_id}_{timestamp}`

| Campo | Tipo | Descricao | Exemplo |
|-------|------|-----------|---------|
| id | string | Identificador unico | "uuid-abc" |
| dealId | string | FK para Deal | "uuid-789" |
| tipo | string | Tipo de interacao | "instagram_dm" |
| canal | string | Canal usado | "instagram" |
| direcao | string | Enviado ou recebido | "enviado" |
| conteudo | string | Resumo da interacao | "DM de apresentacao enviada" |
| resultado | string | Resultado | "aguardando_resposta" |
| data | datetime | Quando ocorreu | "2026-01-12T15:30:00Z" |
| criadoPor | string | Quem registrou | "andre" |

### 2.5 Tabela: Tarefas

**PartitionKey:** `tarefa`
**RowKey:** `{tarefa_id}`

| Campo | Tipo | Descricao | Exemplo |
|-------|------|-----------|---------|
| id | string | Identificador unico | "uuid-def" |
| dealId | string | FK para Deal | "uuid-789" |
| tipo | string | Tipo de tarefa | "seguir_instagram" |
| titulo | string | Descricao curta | "Seguir @oticacristal" |
| dataVencimento | datetime | Prazo | "2026-01-13T18:00:00Z" |
| status | string | Status | "pendente" |
| automatica | boolean | Gerada automaticamente? | true |
| dataConclusao | datetime | Quando foi feita | null |

### 2.6 Tabela: Nutricao

**PartitionKey:** `nutricao`
**RowKey:** `{deal_id}_{sequencia}`

| Campo | Tipo | Descricao | Exemplo |
|-------|------|-----------|---------|
| id | string | Identificador unico | "uuid-ghi" |
| dealId | string | FK para Deal | "uuid-789" |
| canal | string | Canal de nutricao | "email" |
| sequencia | number | Numero na sequencia | 1 |
| template | string | Template usado | "email_erro_2mil" |
| dataEnvio | datetime | Quando foi enviado | "2026-01-14T09:00:00Z" |
| status | string | Status | "enviado" |
| aberto | boolean | Email foi aberto? | true |
| clicou | boolean | Clicou em algum link? | false |

---

## 3. LAYOUT DAS PAGINAS

### 3.1 Dashboard Principal

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  WFINANCE │ Comercial                                    [Andre] [Config]   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  BOM DIA, ANDRE                                      13 Jan 2026    │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐       │
│  │  LEADS       │ │  EM NUTRICAO │ │  PROPOSTAS   │ │  FECHADOS    │       │
│  │     95       │ │      42      │ │      2       │ │      0       │       │
│  │  T1 ativos   │ │   recebendo  │ │   abertas    │ │   janeiro    │       │
│  └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘       │
│                                                                              │
│  ┌─────────────────────────────────┐ ┌─────────────────────────────────┐   │
│  │  TAREFAS HOJE              (8)  │ │  NUTRICAO HOJE                  │   │
│  │                                 │ │                                  │   │
│  │  [ ] Enviar DM @oticacristal   │ │  4 emails programados            │   │
│  │  [ ] Curtir posts @oticavida   │ │  2 broadcasts WhatsApp           │   │
│  │  [ ] Follow-up Otica Sol       │ │                                  │   │
│  │  [ ] Visitar Otica Luz         │ │  [Ver detalhes]                  │   │
│  │                                 │ │                                  │   │
│  │  [Ver todas]                    │ │                                  │   │
│  └─────────────────────────────────┘ └─────────────────────────────────┘   │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  PIPELINE                                            [+ Novo Lead]  │   │
│  │                                                                     │   │
│  │  Captacao    Aquecimento    Contato    Qualificado    Proposta     │   │
│  │  ─────────   ───────────    ───────    ───────────    ────────     │   │
│  │                                                                     │   │
│  │  ┌───────┐   ┌───────┐     ┌───────┐   ┌───────┐     ┌───────┐    │   │
│  │  │Otica A│   │Otica D│     │Otica G│   │Otica I│     │Otica J│    │   │
│  │  │ T1 92 │   │ T1 88 │     │ T1 85 │   │ T1 90 │     │R$1.197│    │   │
│  │  └───────┘   └───────┘     └───────┘   └───────┘     └───────┘    │   │
│  │  ┌───────┐   ┌───────┐     ┌───────┐                              │   │
│  │  │Otica B│   │Otica E│     │Otica H│                              │   │
│  │  │ T1 89 │   │ T1 86 │     │ T1 82 │                              │   │
│  │  └───────┘   └───────┘     └───────┘                              │   │
│  │  ┌───────┐   ┌───────┐                                            │   │
│  │  │Otica C│   │Otica F│                                            │   │
│  │  │ T1 87 │   │ T1 84 │                                            │   │
│  │  └───────┘   └───────┘                                            │   │
│  │                                                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 3.2 Card do Lead (no Kanban)

```
┌─────────────────────────────┐
│  OTICA CRISTAL         T1  │
│  ────────────────────────  │
│  Score: 92  │  ★ 4.7       │
│  @oticacristal             │
│  ────────────────────────  │
│  Joao Silva (dono)         │
│  (82) 99999-8888           │
│  ────────────────────────  │
│  ⏰ Enviar DM (hoje)       │
│  📧 Email 1/4 enviado      │
│                            │
│  [Abrir]  [WhatsApp]  [IG] │
└─────────────────────────────┘
```

### 3.3 Painel Lateral (Detalhes do Lead)

```
┌─────────────────────────────────────────────────┐
│  OTICA CRISTAL                              [X] │
├─────────────────────────────────────────────────┤
│                                                 │
│  ┌───────────────────────────────────────────┐ │
│  │  INFORMACOES                              │ │
│  │                                           │ │
│  │  Status: Aquecimento (3 dias)             │ │
│  │  Score: 92  │  Tier: T1  │  ★ 4.7        │ │
│  │                                           │ │
│  │  EMPRESA                                  │ │
│  │  CNPJ: 12.345.678/0001-90                │ │
│  │  Tel: (82) 3333-4444                     │ │
│  │  Email: contato@oticacristal.com         │ │
│  │  Instagram: @oticacristal                │ │
│  │  Endereco: Rua X, 123 - Pajucara         │ │
│  │                                           │ │
│  │  DECISOR                                  │ │
│  │  Joao Silva (Proprietario)               │ │
│  │  WhatsApp: (82) 99999-8888               │ │
│  │  Email: joao@gmail.com                   │ │
│  └───────────────────────────────────────────┘ │
│                                                 │
│  ┌───────────────────────────────────────────┐ │
│  │  ACOES RAPIDAS                            │ │
│  │                                           │ │
│  │  [Abrir Instagram]  [Abrir WhatsApp]     │ │
│  │  [Enviar Email]     [Agendar Visita]     │ │
│  │  [Registrar Interacao]                   │ │
│  │  [Mover para: ▼]                         │ │
│  └───────────────────────────────────────────┘ │
│                                                 │
│  ┌───────────────────────────────────────────┐ │
│  │  NUTRICAO                                 │ │
│  │                                           │ │
│  │  Email 1/4: Enviado ✓ (abriu)            │ │
│  │  Email 2/4: Agendado 16/jan              │ │
│  │  WhatsApp Biz: Nao enviado               │ │
│  │                                           │ │
│  │  [Pausar nutricao]  [Pular etapa]        │ │
│  └───────────────────────────────────────────┘ │
│                                                 │
│  ┌───────────────────────────────────────────┐ │
│  │  TAREFAS                                  │ │
│  │                                           │ │
│  │  [ ] Enviar DM (hoje)                    │ │
│  │  [✓] Curtir 3 posts (ontem)              │ │
│  │  [✓] Seguir perfil (12/jan)              │ │
│  │                                           │ │
│  │  [+ Nova tarefa]                         │ │
│  └───────────────────────────────────────────┘ │
│                                                 │
│  ┌───────────────────────────────────────────┐ │
│  │  HISTORICO                                │ │
│  │                                           │ │
│  │  13/jan 10:00 - Email 1 enviado          │ │
│  │  12/jan 15:30 - Curtiu 3 posts           │ │
│  │  12/jan 14:00 - Seguiu no Instagram      │ │
│  │  10/jan 09:00 - Lead captado (discovery) │ │
│  │                                           │ │
│  │  [Ver historico completo]                │ │
│  └───────────────────────────────────────────┘ │
│                                                 │
│  ┌───────────────────────────────────────────┐ │
│  │  NOTAS                                    │ │
│  │                                           │ │
│  │  "Loja bem avaliada, parece ter bom      │ │
│  │   movimento. Dono ativo no Instagram."   │ │
│  │                                           │ │
│  │  [Editar]                                │ │
│  └───────────────────────────────────────────┘ │
│                                                 │
└─────────────────────────────────────────────────┘
```

### 3.4 Modal: Registrar Interacao

```
┌─────────────────────────────────────────────────┐
│  REGISTRAR INTERACAO                        [X] │
├─────────────────────────────────────────────────┤
│                                                 │
│  Lead: Otica Cristal                           │
│                                                 │
│  Tipo de Interacao:                            │
│  ┌─────────────────────────────────────────┐   │
│  │ [●] Instagram DM                        │   │
│  │ [ ] WhatsApp                            │   │
│  │ [ ] Ligacao                             │   │
│  │ [ ] Visita presencial                   │   │
│  │ [ ] Email                               │   │
│  │ [ ] Score/Simulador realizado           │   │
│  └─────────────────────────────────────────┘   │
│                                                 │
│  Direcao:                                      │
│  [●] Enviado  [ ] Recebido                     │
│                                                 │
│  Resumo:                                       │
│  ┌─────────────────────────────────────────┐   │
│  │ DM de apresentacao enviada conforme     │   │
│  │ template padrao.                        │   │
│  │                                         │   │
│  └─────────────────────────────────────────┘   │
│                                                 │
│  Resultado:                                    │
│  ┌─────────────────────────────────────────┐   │
│  │ Aguardando resposta               ▼     │   │
│  └─────────────────────────────────────────┘   │
│                                                 │
│  Proxima acao:                                 │
│  ┌─────────────────────────────────────────┐   │
│  │ Follow-up em 3 dias se nao responder ▼  │   │
│  └─────────────────────────────────────────┘   │
│                                                 │
│            [Cancelar]  [Salvar]                │
│                                                 │
└─────────────────────────────────────────────────┘
```

### 3.5 Pagina: Nutricao

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  WFINANCE │ Comercial > Nutricao                         [Andre] [Config]   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  VISAO GERAL DA NUTRICAO                                            │   │
│  │                                                                     │   │
│  │  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐                │   │
│  │  │ EM NUTRICAO  │ │ EMAILS HOJE  │ │  WHATSAPP    │                │   │
│  │  │     42       │ │      4       │ │    HOJE: 0   │                │   │
│  │  │    leads     │ │  agendados   │ │  proximo: 15/jan              │   │
│  │  └──────────────┘ └──────────────┘ └──────────────┘                │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  SEQUENCIA DE EMAILS                                   [Editar]     │   │
│  │                                                                     │   │
│  │  Email 1: "O erro que faz oticas perderem R$ 2mil/mes"             │   │
│  │  ├── Enviados: 42  │  Abertos: 28 (67%)  │  Cliques: 8 (19%)       │   │
│  │                                                                     │   │
│  │  Email 2: "Checklist: seu financeiro esta saudavel?"               │   │
│  │  ├── Enviados: 28  │  Abertos: 18 (64%)  │  Cliques: 5 (18%)       │   │
│  │                                                                     │   │
│  │  Email 3: "Como uma otica de Maceio organizou o crediario"         │   │
│  │  ├── Enviados: 12  │  Abertos: 7 (58%)   │  Cliques: 2 (17%)       │   │
│  │                                                                     │   │
│  │  Email 4: Newsletter mensal                                        │   │
│  │  ├── Enviados: 0   │  Proximo: 01/fev                              │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  BROADCASTS WHATSAPP                                   [Novo]       │   │
│  │                                                                     │   │
│  │  15/jan - Checklist PDF                                            │   │
│  │  ├── Lista: T1 Aquecimento (35 contatos)                           │   │
│  │  ├── Status: Agendado                                              │   │
│  │                                                                     │   │
│  │  01/fev - Caso de sucesso                                          │   │
│  │  ├── Lista: Todos T1 (95 contatos)                                 │   │
│  │  ├── Status: Rascunho                                              │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  LEADS EM NUTRICAO                                     [Filtrar]    │   │
│  │                                                                     │   │
│  │  Lead              │ Etapa Email │ WhatsApp │ Ultimo Engajamento   │   │
│  │  ──────────────────┼─────────────┼──────────┼────────────────────  │   │
│  │  Otica Cristal     │ 2/4         │ Pendente │ Abriu email (hoje)   │   │
│  │  Otica Vida        │ 1/4         │ Enviado  │ Nenhum               │   │
│  │  Otica Sol         │ 3/4         │ Enviado  │ Clicou link (ontem)  │   │
│  │  Otica Luz         │ 1/4         │ Pendente │ Nenhum               │   │
│  │  ...               │             │          │                      │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 3.6 Pagina: Metricas

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  WFINANCE │ Comercial > Metricas                         [Andre] [Config]   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  Periodo: [Janeiro 2026 ▼]                                                  │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  FUNIL DE CONVERSAO                                                 │   │
│  │                                                                     │   │
│  │  Captacao        ████████████████████████████████████████  95      │   │
│  │  Aquecimento     ██████████████████████████████            65 (68%)│   │
│  │  Contato         ████████████████                          35 (54%)│   │
│  │  Qualificado     ████████                                  15 (43%)│   │
│  │  Proposta        ████                                       5 (33%)│   │
│  │  Fechado         ██                                         2 (40%)│   │
│  │                                                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────────────────────┐ ┌──────────────────────────────────┐     │
│  │  TAXAS DE CONVERSAO          │ │  TEMPO MEDIO POR ETAPA           │     │
│  │                              │ │                                  │     │
│  │  Captacao → Aquecimento: 68% │ │  Aquecimento: 3.2 dias          │     │
│  │  Aquecimento → Contato:  54% │ │  Contato: 5.1 dias              │     │
│  │  Contato → Qualificado:  43% │ │  Qualificado: 2.8 dias          │     │
│  │  Qualificado → Proposta: 33% │ │  Proposta: 4.5 dias             │     │
│  │  Proposta → Fechado:     40% │ │                                  │     │
│  │                              │ │  Ciclo total: 15.6 dias         │     │
│  │  TOTAL: Captacao→Fechado: 2% │ │                                  │     │
│  └──────────────────────────────┘ └──────────────────────────────────┘     │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │  RESULTADOS DO MES                                                  │   │
│  │                                                                     │   │
│  │  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐                │   │
│  │  │  PROPOSTAS   │ │   FECHADOS   │ │ FATURAMENTO  │                │   │
│  │  │      5       │ │      2       │ │  R$ 2.394    │                │   │
│  │  │  R$ 5.985    │ │   40% taxa   │ │   previsto   │                │   │
│  │  └──────────────┘ └──────────────┘ └──────────────┘                │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 4. AUTOMACOES

### 4.1 Tarefas Automaticas por Etapa

| Etapa | Gatilho | Tarefa Criada | Prazo |
|-------|---------|---------------|-------|
| **Captacao** | Lead entra | "Mover para aquecimento" | Imediato |
| **Aquecimento** | Entra na etapa | "Seguir no Instagram" | Hoje |
| **Aquecimento** | +1 dia | "Curtir 3 posts" | +1 dia |
| **Aquecimento** | +2 dias | "Reagir stories" | +2 dias |
| **Aquecimento** | +3 dias | "Enviar DM" | +3 dias |
| **Contato** | DM enviada | "Verificar resposta" | +2 dias |
| **Contato** | +5 dias sem resposta | "Agendar visita presencial" | +5 dias |
| **Qualificado** | Entra na etapa | "Realizar Score/Simulador" | +1 dia |
| **Proposta** | Proposta enviada | "Follow-up D+2" | +2 dias |
| **Proposta** | +4 dias | "Follow-up D+4" | +4 dias |
| **Proposta** | +6 dias | "Ultimo contato (vence amanha)" | +6 dias |

### 4.2 Nutricao Automatica

```
LEAD ENTRA EM NUTRICAO
        │
        ▼
┌─────────────────────────────────────────────────────────────┐
│  DIA 0: Email 1 - "O erro que faz oticas perderem..."      │
├─────────────────────────────────────────────────────────────┤
│  DIA 7: Email 2 - "Checklist: seu financeiro..."           │
│         + WhatsApp Biz: Checklist PDF                       │
├─────────────────────────────────────────────────────────────┤
│  DIA 14: Email 3 - "Como uma otica de Maceio..."           │
├─────────────────────────────────────────────────────────────┤
│  DIA 21: Email 4 - Newsletter mensal                       │
│          + WhatsApp Biz: Dica do mes                       │
├─────────────────────────────────────────────────────────────┤
│  MENSAL: Continua recebendo newsletter + broadcast         │
└─────────────────────────────────────────────────────────────┘
        │
        │  SE EM QUALQUER MOMENTO:
        │  - Abrir email + clicar
        │  - Responder WhatsApp
        │  - Responder DM
        │
        ▼
┌─────────────────────────────────────────────────────────────┐
│  ALERTA: "Lead engajou! Contato prioritario"               │
│  Move para: CONTATO                                        │
│  Tarefa: "Enviar WhatsApp pessoal"                         │
└─────────────────────────────────────────────────────────────┘
```

### 4.3 Notificacoes (Telegram/WhatsApp)

**Diaria (9h):**
```
📋 TAREFAS DO DIA - 13/01

🔥 AQUECIMENTO:
• Enviar DM - Otica Cristal (@oticacristal)
• Curtir posts - Otica Vida (@oticavida)

📞 FOLLOW-UP:
• Proposta D+2 - Otica Sol

⚠️ ATENCAO:
• Lead esfriando - Otica Luz (5 dias sem resposta)

📧 NUTRICAO HOJE:
• 4 emails agendados
• 0 broadcasts

────────────────
Total: 8 tarefas
```

**Alertas em tempo real:**
```
🔔 LEAD ENGAJOU!

Otica Cristal abriu o email e clicou no link.

Acao recomendada: Enviar WhatsApp pessoal agora.

[Abrir lead] [Copiar msg WhatsApp]
```

---

## 5. FLUXOS DE USUARIO

### 5.1 Adicionar Lead Manualmente

```
1. Clicar [+ Novo Lead]
2. Preencher dados da empresa
3. Preencher dados do decisor
4. Definir Tier (T1/T2/T3)
5. Escolher etapa inicial
6. Salvar
7. Sistema cria tarefas automaticas
8. Lead aparece no Kanban
```

### 5.2 Mover Lead no Pipeline

```
1. Arrastar card no Kanban
   OU
   Clicar no card > "Mover para: [etapa]"
2. Sistema registra mudanca no historico
3. Sistema cria tarefas da nova etapa
4. Se "Proposta" > Pedir valor estimado
5. Se "Fechado Ganho" > Pedir dados do contrato
6. Se "Fechado Perdido" > Pedir motivo
```

### 5.3 Registrar Interacao

```
1. Abrir lead
2. Clicar [Registrar Interacao]
3. Selecionar tipo (DM, WhatsApp, Visita, etc)
4. Preencher resumo
5. Selecionar resultado
6. Definir proxima acao
7. Salvar
8. Sistema atualiza historico
9. Sistema cria tarefa se necessario
```

### 5.4 Completar Tarefa

```
1. Na lista de tarefas, clicar no checkbox
   OU
   No card do lead, clicar na tarefa
2. Sistema marca como concluida
3. Sistema pergunta resultado (se aplicavel)
4. Sistema cria proxima tarefa (se configurado)
```

---

## 6. INTEGRACOES

### 6.1 Azure Table Storage
- Todas as tabelas no Azure
- Queries otimizadas por PartitionKey
- Backup automatico

### 6.2 SendGrid/Resend (Email)
- Envio de emails da sequencia
- Tracking de abertura e cliques
- Webhook para atualizar status

### 6.3 WhatsApp Business (Manual inicial)
- Links diretos para abrir conversa
- Templates de mensagem para copiar
- Futuro: API para automacao

### 6.4 Telegram Bot (Notificacoes)
- Tarefas diarias
- Alertas de engajamento
- Comandos para marcar tarefas

### 6.5 Instagram (Links)
- Link direto para perfil
- Link direto para DM
- Futuro: API para metricas

---

## 7. TEMPLATES DE MENSAGEM

### 7.1 DM Instagram - Primeiro Contato
```
Oi [nome]! Vi que a [otica] tem otima avaliacao no Google.

Trabalho com gestao financeira especializada em oticas aqui em Maceio.
Tenho um material sobre controle de crediario que pode te ajudar.

Posso enviar?
```

### 7.2 WhatsApp - Apos DM Positiva
```
Oi [nome], aqui e o Andre da WFinance!

Conforme combinamos no Instagram, segue o checklist de saude financeira para oticas.

Da uma olhada com calma. Qualquer duvida, me chama aqui!
```

### 7.3 WhatsApp - Agendar Score/Simulador
```
[nome], tudo bem?

Vi que voce curtiu o material! Posso fazer uma simulacao rapida (10 min)
de quanto voce economizaria com uma gestao financeira organizada?

Sem compromisso. Que tal [dia] as [hora]?
```

### 7.4 WhatsApp - Envio de Proposta
```
[nome], conforme conversamos, segue a proposta da WFinance pra [otica].

Montei pensando nas dores que voce me contou:
- [dor 1]
- [dor 2]

Qualquer duvida, me chama!
```

### 7.5 WhatsApp - Follow-up Proposta
```
Oi [nome]! Conseguiu dar uma olhada na proposta?

Fico a disposicao pra tirar qualquer duvida.
```

---

## 8. PERMISSOES E CONFIGURACOES

### 8.1 Configuracoes do Sistema
- Horario de envio de emails (padrao: 9h)
- Horario de notificacao diaria (padrao: 9h)
- Dias de aquecimento antes de DM (padrao: 3)
- Dias para follow-up de proposta (padrao: 2, 4, 6)
- Canal de notificacao (Telegram/WhatsApp)

### 8.2 Templates Editaveis
- Todos os templates de mensagem
- Sequencia de emails
- Mensagens de broadcast

---

## 9. PROXIMOS PASSOS PARA DESENVOLVIMENTO

### Fase 1: MVP (Prioridade Alta)
- [ ] Estrutura de dados no Azure Table Storage
- [ ] Tela de Pipeline (Kanban)
- [ ] Card do lead com informacoes basicas
- [ ] Painel lateral com detalhes
- [ ] Mover lead entre etapas
- [ ] Lista de tarefas manuais

### Fase 2: Automacao (Prioridade Media)
- [ ] Geracao automatica de tarefas por etapa
- [ ] Integracao com SendGrid/Resend
- [ ] Notificacoes via Telegram
- [ ] Tracking de emails (abertura/clique)

### Fase 3: Nutricao (Prioridade Media)
- [ ] Configuracao de sequencia de emails
- [ ] Disparo automatico baseado em dias
- [ ] Alertas de engajamento
- [ ] Dashboard de nutricao

### Fase 4: Metricas (Prioridade Baixa)
- [ ] Funil de conversao
- [ ] Taxas por etapa
- [ ] Tempo medio por etapa
- [ ] Relatorios mensais

---

## 10. WIREFRAMES ADICIONAIS

### 10.1 Mobile - Lista de Tarefas
```
┌─────────────────────────┐
│  ≡  TAREFAS      [+]    │
├─────────────────────────┤
│                         │
│  HOJE (8)               │
│  ─────────────────────  │
│                         │
│  [ ] Enviar DM          │
│      Otica Cristal      │
│      ⏰ Vence hoje       │
│                         │
│  [ ] Curtir posts       │
│      Otica Vida         │
│      ⏰ Vence hoje       │
│                         │
│  [ ] Follow-up          │
│      Otica Sol          │
│      ⏰ Vence hoje       │
│                         │
│  AMANHA (3)             │
│  ─────────────────────  │
│                         │
│  [ ] Enviar DM          │
│      Otica Luz          │
│                         │
│  [ ] Visitar            │
│      Otica Mar          │
│                         │
└─────────────────────────┘
```

### 10.2 Mobile - Card do Lead
```
┌─────────────────────────┐
│  ←  OTICA CRISTAL       │
├─────────────────────────┤
│                         │
│  Status: Aquecimento    │
│  Score: 92 │ T1 │ ★ 4.7 │
│                         │
│  ─────────────────────  │
│                         │
│  ACOES RAPIDAS          │
│                         │
│  [Instagram] [WhatsApp] │
│  [Email]    [Ligar]     │
│                         │
│  ─────────────────────  │
│                         │
│  TAREFA PENDENTE        │
│  [ ] Enviar DM (hoje)   │
│                         │
│  ─────────────────────  │
│                         │
│  DECISOR                │
│  Joao Silva             │
│  (82) 99999-8888        │
│                         │
│  ─────────────────────  │
│                         │
│  [Registrar Interacao]  │
│  [Mover Etapa]          │
│                         │
└─────────────────────────┘
```

---

*Especificacao v1.0 - 13/01/2026*
*Pronto para desenvolvimento*
