# PROCESSO COMERCIAL OPERACIONAL
## WFinance | Guia de Execucao Diaria

**Versao:** 1.0 | **Atualizado:** 13/01/2026

---

## PIPELINE VISUAL

```
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                              PIPELINE COMERCIAL WFINANCE                                 │
├─────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                          │
│  📥 CAPTACAO     🔥 AQUECIMENTO    💬 CONTATO      🎯 QUALIFICADO    💰 FECHAMENTO      │
│  (Sistema)       (2-3 dias)        (DM/Visita)     (Diagnostico)     (Proposta)         │
│                                                                                          │
│  ┌─────────┐    ┌─────────┐       ┌─────────┐     ┌─────────┐       ┌─────────┐        │
│  │         │    │         │       │         │     │         │       │         │        │
│  │  Lead   │───>│ Seguir  │──────>│   DM    │────>│  Diag   │──────>│ Proposta│        │
│  │  T1/T2  │    │ Curtir  │       │ Visita  │     │ Agendado│       │ Enviada │        │
│  │         │    │ Engajar │       │         │     │         │       │         │        │
│  └─────────┘    └─────────┘       └─────────┘     └─────────┘       └─────────┘        │
│       │              │                 │               │                 │              │
│       ▼              ▼                 ▼               ▼                 ▼              │
│    Azure         Instagram          WhatsApp        Reuniao          Contrato          │
│                                                                                          │
└─────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## KANBAN - STATUS DOS LEADS

### 📥 CAPTACAO (Leads Novos)
| # | Otica | Score | Rating | Instagram | Acao |
|---|-------|-------|--------|-----------|------|
| _ | _____ | _____ | ______ | _________ | [ ] Mover para Aquecimento |

### 🔥 AQUECIMENTO (Seguindo/Engajando)
| # | Otica | Instagram | Seguiu | Curtiu | Stories | Dias | Acao |
|---|-------|-----------|--------|--------|---------|------|------|
| _ | _____ | _________ | [ ]    | [ ]    | [ ]     | _/3  | [ ] Mover para Contato |

### 💬 CONTATO (DM Enviada / Visita)
| # | Otica | Tipo | Data | Resposta | Proxima Acao |
|---|-------|------|------|----------|--------------|
| _ | _____ | DM/Visita | __/__ | Sim/Nao/Aguardando | ____________ |

### 🎯 QUALIFICADO (Diagnostico)
| # | Otica | Data Diag | Dores Identificadas | Proposta? |
|---|-------|-----------|---------------------|-----------|
| _ | _____ | __/__     | ________________    | [ ] Sim   |

### 💰 FECHAMENTO (Proposta Enviada)
| # | Otica | Valor | Data Envio | Follow-up | Status |
|---|-------|-------|------------|-----------|--------|
| _ | _____ | R$___ | __/__      | __/__     | Aberto/Ganho/Perdido |

### ✅ CLIENTES FECHADOS
| # | Otica | Pacote | Valor | Data Inicio |
|---|-------|--------|-------|-------------|
| _ | _____ | ______ | R$___ | __/__       |

---

## ETAPAS DETALHADAS COM CHECKLISTS

---

### ETAPA 1: CAPTACAO
**Responsavel:** Sistema | **Frequencia:** Semanal

```
┌────────────────────────────────────────────────┐
│  📥 CAPTACAO                                   │
│                                                │
│  CNAE + Regiao + Google Maps                   │
│           │                                    │
│           ▼                                    │
│  ┌──────────────────────┐                     │
│  │ Classificacao        │                     │
│  │ T1: Score 85-100     │ ← Prioridade        │
│  │ T2: Score 70-84      │                     │
│  │ T3: Score < 70       │                     │
│  └──────────────────────┘                     │
│           │                                    │
│           ▼                                    │
│     Azure Table Storage                        │
└────────────────────────────────────────────────┘
```

**Checklist Semanal:**
- [ ] Rodar discovery de novos leads
- [ ] Verificar duplicados (mesmo CNPJ)
- [ ] Remover falsos positivos
- [ ] Extrair Top 20 T1 da semana
- [ ] Atualizar planilha de tracking

**Criterios T1 (Prioridade Maxima):**
- [ ] Score 85+
- [ ] Rating Google 4.5+
- [ ] Localizacao: Maceio/AL
- [ ] Sem "Recuperacao Judicial"
- [ ] Nao e franquia grande

---

### ETAPA 2: SELECAO
**Responsavel:** Andre | **Tempo:** 30-60 min/semana

```
┌────────────────────────────────────────────────┐
│  🎯 SELECAO TOP 20                             │
│                                                │
│  Filtrar    →   Mapear     →   Priorizar      │
│  Score 85+      Instagram      Por potencial  │
└────────────────────────────────────────────────┘
```

**Checklist:**
- [ ] Filtrar leads T1 do Azure (Score 85+)
- [ ] Verificar Rating Google (4.5+)
- [ ] Buscar Instagram de cada otica
- [ ] Anotar @ na planilha
- [ ] Ordenar por potencial (rating + engajamento)

**Template de Registro:**
```
Otica: _____________
CNPJ: ______________
Score: _____
Rating: _____ estrelas
Endereco: __________
Instagram: @________
Observacoes: _______
```

---

### ETAPA 3: AQUECIMENTO
**Responsavel:** Andre | **Duracao:** 2-3 dias por lead

```
┌────────────────────────────────────────────────┐
│  🔥 AQUECIMENTO                                │
│                                                │
│  Dia 1         Dia 2         Dia 3            │
│  ┌─────┐      ┌─────┐       ┌─────┐           │
│  │Seguir│ ──> │Curtir│ ───> │Story │           │
│  │     │      │2-3   │      │React │           │
│  └─────┘      └─────┘       └─────┘           │
│                                │               │
│                                ▼               │
│                          Pronto pra DM        │
└────────────────────────────────────────────────┘
```

**Checklist por Lead:**
- [ ] Seguir perfil no Instagram
- [ ] Curtir 2-3 posts recentes
- [ ] Reagir a stories (se tiver)
- [ ] Aguardar 2-3 dias
- [ ] Verificar se seguiu de volta
- [ ] Marcar como "Pronto para DM"

**Ritmo Recomendado:**
| Dia | Acao | Volume |
|-----|------|--------|
| Seg | Seguir novos perfis | 5 perfis |
| Ter | Curtir posts | 10-15 curtidas |
| Qua | Reagir stories | 3-5 reacoes |
| Qui | Seguir novos perfis | 5 perfis |
| Sex | Revisar engajamento | - |

---

### ETAPA 4: PRIMEIRO CONTATO (DM)
**Responsavel:** Andre | **Tempo:** 5 min por DM

```
┌────────────────────────────────────────────────┐
│  💬 PRIMEIRO CONTATO                           │
│                                                │
│  ┌──────────────────────────────────────────┐ │
│  │                                          │ │
│  │  "Oi [nome]! Vi que a [otica] tem       │ │
│  │   otima avaliacao no Google.            │ │
│  │                                          │ │
│  │   Trabalho com gestao financeira        │ │
│  │   especializada em oticas aqui          │ │
│  │   em Maceio.                            │ │
│  │                                          │ │
│  │   Tenho um material sobre controle      │ │
│  │   de crediario que pode te ajudar.      │ │
│  │                                          │ │
│  │   Posso enviar?"                        │ │
│  │                                          │ │
│  └──────────────────────────────────────────┘ │
│                                                │
│  Tom: Leve, pede permissao, oferece valor     │
└────────────────────────────────────────────────┘
```

**Checklist antes de enviar DM:**
- [ ] Lead foi aquecido por 2-3 dias?
- [ ] Personalizei com nome da otica?
- [ ] Mencionei avaliacao do Google?
- [ ] Tom esta leve (nao vendedor)?

**Registro apos envio:**
```
Otica: _____________
Data DM: __/__/____
Hora: _____
Resposta: [ ] Sim  [ ] Nao  [ ] Aguardando
Data Resposta: __/__/____
Proximo passo: ______________
```

---

### ETAPA 5: NUTRICAO
**Responsavel:** Andre | **Varia por cenario**

```
┌────────────────────────────────────────────────┐
│  🌱 NUTRICAO - CENARIOS                        │
│                                                │
│  RESPOSTA           ACAO                       │
│  ─────────────────────────────────────────     │
│                                                │
│  ✅ Positiva   ──>  Enviar material            │
│                     Continuar conversa         │
│                     Migrar pra WhatsApp        │
│                     Oferecer diagnostico       │
│                                                │
│  😶 Sem resposta ─> Esperar 3-5 dias           │
│                     Visita presencial          │
│                                                │
│  ❌ Negativa   ──>  Agradecer                  │
│                     Manter na lista longo      │
│                     prazo (nurturing 3 meses)  │
└────────────────────────────────────────────────┘
```

**Se Resposta Positiva - Checklist:**
- [ ] Enviar material de valor (Checklist PDF)
- [ ] Agradecer o interesse
- [ ] Fazer pergunta sobre dor ("Como ta o controle de crediario ai?")
- [ ] Propor migrar pra WhatsApp
- [ ] Agendar diagnostico

**Template - Resposta Positiva:**
```
Que bom! Segue o checklist de saude financeira.

Da uma olhada com calma. Geralmente donos de
otica se identificam com uns 5-6 itens ali.

Se quiser, posso fazer um diagnostico rapido
(30 min) pra te mostrar onde da pra melhorar.

Sem compromisso. Quer marcar?
```

**Template - Migrando pra WhatsApp:**
```
Perfeito! Pra facilitar, podemos continuar
pelo WhatsApp?

Meu numero: (XX) XXXXX-XXXX

Ou me passa o seu que eu te chamo.
```

---

### ETAPA 6: VISITA PRESENCIAL
**Responsavel:** Andre | **Tempo:** 30 min por visita

```
┌────────────────────────────────────────────────┐
│  🚶 VISITA PRESENCIAL                          │
│                                                │
│  ANTES          DURANTE         DEPOIS        │
│  ┌─────┐       ┌─────┐         ┌─────┐        │
│  │Mapa │       │Pitch│         │Anotar│       │
│  │Rota │  ──>  │2min │   ──>   │CRM   │       │
│  │Hora │       │     │         │      │       │
│  └─────┘       └─────┘         └─────┘        │
└────────────────────────────────────────────────┘
```

**Pitch 2 Minutos - Estrutura:**
```
┌──────────────────────────────────────────────────────────┐
│  🎤 PITCH 2 MINUTOS                                      │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  1. QUEM SOU (10 seg)                                   │
│     "Oi, sou Andre da WFinance.                         │
│      Trabalho com gestao financeira pra oticas."        │
│                                                          │
│  2. PROBLEMA (20 seg)                                   │
│     "Sei que dono de otica vive apagando incendio       │
│      no financeiro. Crediario atrasado, conta que       │
│      aparece do nada, fluxo de caixa bagunçado..."      │
│                                                          │
│  3. SOLUCAO (20 seg)                                    │
│     "Cuido de todo o financeiro pra voce focar          │
│      em vender. Lanço contas, faco conciliacao,         │
│      mando relatorio toda semana."                      │
│                                                          │
│  4. PROVA (20 seg)                                      │
│     "Ja trabalho com uma otica aqui em Maceio           │
│      ha mais de um ano. O dono parou de se              │
│      preocupar com banco e foca so em cliente."         │
│                                                          │
│  5. OFERTA (20 seg)                                     │
│     "Posso fazer um diagnostico gratuito do seu         │
│      financeiro. 30 minutos, sem compromisso.           │
│      Te mostro onde pode melhorar."                     │
│                                                          │
│  6. CTA (10 seg)                                        │
│     "Posso te ligar essa semana pra marcar?"            │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

**Checklist Visita:**
- [ ] Endereco confirmado no mapa
- [ ] Melhor horario (10h-11h ou 15h-16h)
- [ ] Pitch decorado
- [ ] Cartao de visita
- [ ] Material de valor (se tiver)

**Registro pos-visita:**
```
Otica: _____________
Data: __/__/____
Horario: _____
Falou com: _____________
Cargo: _________________
Receptividade: [ ] Alta  [ ] Media  [ ] Baixa
Diagnostico agendado: [ ] Sim  [ ] Nao
Data diagnostico: __/__/____
Observacoes: ___________
```

---

### ETAPA 7: DIAGNOSTICO
**Responsavel:** Andre | **Duracao:** 30-60 min

```
┌────────────────────────────────────────────────┐
│  🔍 DIAGNOSTICO                                │
│                                                │
│  ABERTURA      DESCOBERTA      VALOR          │
│  (5 min)       (20 min)        (10 min)       │
│  ┌─────┐       ┌─────┐         ┌─────┐        │
│  │Rapport│ ──> │Perguntas│ ──> │Mostrar│       │
│  │      │      │Dores    │     │Solucao│       │
│  └─────┘       └─────┘         └─────┘        │
│                                    │          │
│                                    ▼          │
│                            Proposta ou        │
│                            Objecao mapeada    │
└────────────────────────────────────────────────┘
```

**Roteiro de Perguntas:**
```
SITUACAO ATUAL
- Como voce controla o financeiro hoje?
- Quem cuida das contas a pagar e receber?
- Usa algum sistema ou planilha?

DORES
- Qual a maior dor de cabeca financeira?
- Ja teve susto com conta que esqueceu?
- Como ta a inadimplencia no crediario?

IMPACTO
- Quanto tempo voce gasta com financeiro por semana?
- Isso te atrapalha de focar em vender?
- Ja perdeu dinheiro por falta de controle?

SOLUCAO
- Se voce nao precisasse se preocupar com isso,
  o que mudaria no seu dia?
- Quanto vale pra voce ter tranquilidade financeira?
```

**Checklist Diagnostico:**
- [ ] Rapport inicial (perguntar do negocio)
- [ ] Perguntas de situacao
- [ ] Identificar 2-3 dores principais
- [ ] Mostrar como WFinance resolve
- [ ] Verificar interesse
- [ ] Se positivo: agendar envio de proposta
- [ ] Se objecao: anotar e tratar

---

### ETAPA 8: PROPOSTA E FECHAMENTO
**Responsavel:** Andre | **Prazo:** 7 dias max

```
┌────────────────────────────────────────────────┐
│  💰 PROPOSTA E FECHAMENTO                      │
│                                                │
│  CRIAR         ENVIAR        FOLLOW-UP        │
│  (30 min)      (5 min)       (a cada 2 dias)  │
│  ┌─────┐       ┌─────┐       ┌─────┐          │
│  │Custom│ ──>  │WhatsApp│ ──>│Ligar │          │
│  │izada │      │+ PDF  │     │     │          │
│  └─────┘       └─────┘       └─────┘          │
│                                   │            │
│                    ┌──────────────┴──────┐     │
│                    ▼                     ▼     │
│               ✅ GANHO              ❌ PERDIDO │
│               Cliente!              (motivo)   │
└────────────────────────────────────────────────┘
```

**Checklist Proposta:**
- [ ] Personalizar com nome da otica
- [ ] Pacote adequado ao volume
- [ ] Add-ons relevantes
- [ ] Resumo das dores identificadas
- [ ] Beneficios especificos
- [ ] Preco claro
- [ ] Prazo de validade (7 dias)

**Template de Envio:**
```
Oi [nome]!

Conforme conversamos, segue a proposta
da WFinance pra [otica].

Montei pensando nas dores que voce me contou:
- [Dor 1]
- [Dor 2]

Qualquer duvida, me chama.

Abraco,
Andre
```

**Cronograma de Follow-up:**
| Dia | Acao |
|-----|------|
| D+0 | Enviar proposta |
| D+2 | "Conseguiu ver a proposta?" |
| D+4 | "Alguma duvida?" |
| D+6 | "Proposta vence amanha" |
| D+7 | Ultima tentativa / encerrar |

**Se Perder - Registrar:**
```
Otica: _____________
Motivo: [ ] Preco  [ ] Timing  [ ] Nao viu valor
        [ ] Concorrente  [ ] Outro: _______
Retomar em: __/__/____
Aprendizado: ___________
```

---

## METRICAS E METAS

### Dashboard Semanal

```
┌─────────────────────────────────────────────────────────────┐
│                    METRICAS SEMANA __/__                     │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  CAPTACAO          AQUECIMENTO        CONTATO               │
│  ┌─────────┐       ┌─────────┐        ┌─────────┐          │
│  │ __/20   │       │ __/20   │        │ __/15   │          │
│  │ leads   │       │ seguidos│        │ DMs     │          │
│  └─────────┘       └─────────┘        └─────────┘          │
│                                                              │
│  RESPOSTAS         DIAGNOSTICOS       PROPOSTAS             │
│  ┌─────────┐       ┌─────────┐        ┌─────────┐          │
│  │ __/5    │       │ __/3    │        │ __/2    │          │
│  │ positivas│      │ feitos  │        │ enviadas│          │
│  └─────────┘       └─────────┘        └─────────┘          │
│                                                              │
│  CLIENTES FECHADOS                                          │
│  ┌─────────────────────────────────────┐                    │
│  │            __/1                      │                    │
│  └─────────────────────────────────────┘                    │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Metas Janeiro 2026

| Indicador | Meta | Atual | % |
|-----------|------|-------|---|
| Leads T1 filtrados | 20 | __ | __% |
| Perfis seguidos | 20 | __ | __% |
| DMs enviadas | 15 | __ | __% |
| Respostas positivas | 5 | __ | __% |
| Visitas realizadas | 10 | __ | __% |
| Diagnosticos | 3-4 | __ | __% |
| Propostas | 2-3 | __ | __% |
| **Clientes fechados** | **1** | __ | __% |

### Taxas de Conversao (Referencia)

```
Leads T1 ──────────────────────────────────> 100%
    │
    ▼ (tem Instagram)
Perfis Seguidos ───────────────────────────> 75%
    │
    ▼ (DM enviada)
DMs Enviadas ──────────────────────────────> 75%
    │
    ▼ (responde positivo)
Respostas Positivas ───────────────────────> 33%
    │
    ▼ (aceita diagnostico)
Diagnosticos ──────────────────────────────> 30-40%
    │
    ▼ (recebe proposta)
Propostas ─────────────────────────────────> 50-70%
    │
    ▼ (fecha)
CLIENTE ───────────────────────────────────> 30-50%
```

---

## ROTINA DIARIA

### Checklist Diario (10-15 min)

```
┌────────────────────────────────────────────────┐
│  ☀️ MANHA (5 min)                              │
│                                                │
│  [ ] Verificar notificacoes Instagram         │
│  [ ] Responder DMs recebidas                  │
│  [ ] Ver quem seguiu de volta                 │
└────────────────────────────────────────────────┘

┌────────────────────────────────────────────────┐
│  🌙 FIM DO DIA (10 min)                        │
│                                                │
│  [ ] Curtir 3-5 posts de leads aquecendo      │
│  [ ] Reagir a stories                         │
│  [ ] Atualizar planilha de tracking           │
│  [ ] Planejar acoes do dia seguinte           │
└────────────────────────────────────────────────┘
```

### Rotina Semanal

| Dia | Foco | Acoes |
|-----|------|-------|
| **Seg** | Planejamento | Revisar pipeline, definir prioridades |
| **Ter** | Aquecimento | Seguir novos perfis, curtir posts |
| **Qua** | Contato | Enviar DMs, responder conversas |
| **Qui** | Aquecimento | Engajar stories, curtir posts |
| **Sex** | Contato | Enviar DMs, agendar visitas |
| **Sab** | Revisao | Atualizar metricas, ajustar estrategia |
| **Dom** | Descanso | (opcional: planejamento semana) |

---

## MATERIAIS PRONTOS

### Checklist de Saude Financeira (PDF)

```
┌──────────────────────────────────────────────────────────────┐
│  CHECKLIST MENSAL DE SAUDE FINANCEIRA                        │
│  Para Oticas | WFinance                                      │
├──────────────────────────────────────────────────────────────┤
│                                                               │
│  FLUXO DE CAIXA                                              │
│  [ ] Sei exatamente quanto tenho no banco hoje               │
│  [ ] Atualizo entradas e saidas 1x por semana                │
│  [ ] Tenho previsao de caixa para 30 dias                    │
│                                                               │
│  CONTAS A PAGAR                                              │
│  [ ] Sei todas as contas que vencem essa semana              │
│  [ ] Pago fornecedores em dia                                │
│  [ ] Tenho controle de boletos e vencimentos                 │
│                                                               │
│  CONTAS A RECEBER                                            │
│  [ ] Sei quanto tenho de crediario em aberto                 │
│  [ ] Acompanho inadimplencia                                 │
│  [ ] Faco cobranca ativa de atrasados                        │
│                                                               │
│  CONCILIACAO                                                 │
│  [ ] Confiro extrato bancario 1x por semana                  │
│  [ ] Identifico todas as movimentacoes                       │
│  [ ] Nao misturo conta PJ com pessoal                        │
│                                                               │
│  RESULTADO                                                   │
│  12-15 ✓ = Saudavel                                          │
│  8-11 ✓  = Atencao                                           │
│  4-7 ✓   = Alerta                                            │
│  0-3 ✓   = Urgente                                           │
│                                                               │
│  ─────────────────────────────────────────────────────────   │
│  Quer ajuda? Faco diagnostico gratuito de 30 min.            │
│  Andre Paiva | WFinance | (XX) XXXXX-XXXX                    │
└──────────────────────────────────────────────────────────────┘
```

---

## OBJECOES COMUNS E RESPOSTAS

| Objecao | Resposta |
|---------|----------|
| **"Ta caro"** | "Quanto voce perde por mes por falta de controle? Geralmente e mais que o investimento." |
| **"Ja tenho contador"** | "Contador faz imposto. Eu cuido do dia a dia: fluxo, crediario, conciliacao." |
| **"Nao tenho tempo"** | "Justamente! Eu cuido pra voce nao perder tempo. Sao 5 min por semana pra ver o relatorio." |
| **"Vou pensar"** | "Claro! Posso te ligar quinta pra saber?" |
| **"Minha esposa cuida"** | "Otimo! Posso conversar com ela? As vezes ajuda ter um suporte." |

---

## LINKS RAPIDOS

- [Estrategia Janeiro 2026](ESTRATEGIA_JANEIRO_2026.md)
- [Consultoria Comercial](CONSULTORIA_COMERCIAL.md)
- [Estrutura de Precos](Estrutura%20de%20Ofertas%20e%20Precificação%20WFinance.md)
- [Marketing 2026](MARKETING_STRATEGY_2026.md)

---

*Documento operacional - Atualizar semanalmente*
*Versao 1.0 | 13/01/2026*
