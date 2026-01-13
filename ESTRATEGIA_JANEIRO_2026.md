# ESTRATEGIA COMERCIAL - JANEIRO 2026

## WFinance | Guia de Execucao

**Periodo:** 12 a 31 de janeiro/2026
**Meta:** 1-2 clientes pagantes
**Contexto:** Andre embarcado ate 22/jan, depois em Maceio

---

## 1. PROCESSO COMERCIAL DEFINIDO

### 1.1 Visao Geral

```
CAPTACAO        AQUECIMENTO       CONTATO         CONVERSAO
(Sistema)       (Instagram)       (DM + Visita)   (Andre)

┌─────────┐     ┌─────────┐      ┌─────────┐     ┌─────────┐
│ Discovery│     │ Seguir  │      │   DM    │     │Diagnostico
│ CNAE+Maps│────>│ Curtir  │─────>│ Visita  │────>│ Proposta│
│ Score   │     │ Engajar │      │WhatsApp │     │Fechamento
└─────────┘     └─────────┘      └─────────┘     └─────────┘
     │               │                │               │
     ▼               ▼                ▼               ▼
  T1/T2/T3      Relacionamento    Interesse       Cliente
  no Azure      estabelecido      confirmado      pagante
```

### 1.2 Etapas Detalhadas

#### ETAPA 1: Captacao (Automatico)
- **O que:** Sistema busca oticas por CNAE + regiao + Google Maps
- **Resultado:** Lead classificado T1/T2/T3 com score
- **Onde fica:** Azure Table Storage (CommercialLeads)
- **Responsavel:** Sistema

#### ETAPA 2: Selecao (Manual)
- **O que:** Filtrar Top 20 leads T1 para abordagem
- **Criterios:** Score 85+, Rating 4.5+, Maceio, sem RJ
- **Resultado:** Lista priorizada com Instagram mapeado
- **Responsavel:** Andre

#### ETAPA 3: Aquecimento (Manual - Instagram)
- **O que:** Criar presenca antes de abordar
- **Acoes:** Seguir, curtir 2-3 posts, reagir stories
- **Tempo:** 2-3 dias antes da DM
- **Resultado:** Perfil "conhecido" antes do contato
- **Responsavel:** Andre

#### ETAPA 4: Primeiro Contato (Manual - DM)
- **O que:** Mensagem direta no Instagram
- **Tom:** Leve, pede permissao, oferece valor
- **Resultado:** Conversa iniciada ou silencio
- **Responsavel:** Andre

**Template DM:**
```
Oi [nome]! Vi que a [otica] tem otima avaliacao no Google.

Trabalho com gestao financeira especializada em oticas aqui em Maceio.
Tenho um material sobre controle de crediario que pode te ajudar.

Posso enviar?
```

#### ETAPA 5: Nutricao (Manual)
- **Se respondeu positivo:** Enviar material, continuar conversa, migrar pra WhatsApp
- **Se nao respondeu:** Visita presencial quando voltar
- **Se respondeu negativo:** Agradecer, seguir nurturing longo prazo

#### ETAPA 6: Visita Presencial
- **O que:** Ir ate a otica, apresentar-se, pitch de 2 min
- **Objetivo:** Agendar diagnostico gratuito
- **Resultado:** Diagnostico marcado ou cartao deixado
- **Responsavel:** Andre

**Pitch 2 minutos:**
```
1. QUEM SOU (10 seg)
   "Oi, sou Andre da WFinance. Trabalho com gestao financeira pra oticas."

2. PROBLEMA (20 seg)
   "Sei que dono de otica vive apagando incendio no financeiro.
   Crediario atrasado, conta que aparece do nada, fluxo de caixa bagunçado..."

3. SOLUCAO (20 seg)
   "Cuido de todo o financeiro pra voce focar em vender.
   Lanço contas, faco conciliacao, mando relatorio toda semana."

4. PROVA (20 seg)
   "Ja trabalho com uma otica aqui em Maceio ha mais de um ano.
   O dono parou de se preocupar com banco e foca so em cliente."

5. OFERTA (20 seg)
   "Posso fazer um diagnostico gratuito do seu financeiro.
   30 minutos, sem compromisso. Te mostro onde pode melhorar."

6. CTA (10 seg)
   "Posso te ligar essa semana pra marcar?"
```

#### ETAPA 7: Diagnostico
- **O que:** Conversa de 30-60 min (presencial ou call)
- **Objetivo:** Entender situacao, mostrar valor, apresentar proposta
- **Resultado:** Proposta enviada ou objecao mapeada
- **Responsavel:** Andre

#### ETAPA 8: Proposta e Fechamento
- **O que:** Enviar proposta formal, negociar, fechar
- **Prazo:** Maximo 7 dias entre proposta e decisao
- **Resultado:** Cliente fechado ou perdido (com motivo)
- **Responsavel:** Andre

---

## 2. FERRAMENTAS

### 2.1 Ferramentas Atuais (Ja tem)

| Ferramenta | Uso | Status |
|------------|-----|--------|
| **Azure Table Storage** | Base de leads (CommercialLeads) | Funcional |
| **Sistema Discovery** | Captacao automatica de leads | Funcional |
| **Instagram pessoal** | Aquecimento e DMs | Usar |
| **WhatsApp pessoal** | Conversas apos primeiro contato | Usar |
| **HubSpot CRM** | Gestao do pipeline | Em configuracao |

### 2.2 Ferramentas a Configurar

| Ferramenta | Uso | Quando |
|------------|-----|--------|
| **Planilha Google Sheets** | Tracking manual dos 20 leads | 14/jan |
| **Canva** | Criar material de valor (checklist) | 21/jan |
| **LinkedIn** | Perfil profissional | 20/jan |
| **Calendly** (opcional) | Agendamento de diagnosticos | Fev |

### 2.3 Estrutura da Planilha de Tracking

Criar no Google Sheets:

| Coluna | Descricao |
|--------|-----------|
| # | Numero sequencial |
| Otica | Nome fantasia |
| CNPJ | Identificador |
| Score | Score do sistema |
| Rating Google | Nota no Google |
| Endereco | Localizacao |
| Instagram | @perfil |
| Status Insta | Seguiu / Curtiu / DM enviada |
| Data DM | Quando enviou |
| Resposta | Positiva / Negativa / Sem resposta |
| Visita | Data da visita |
| Diagnostico | Agendado / Realizado |
| Proposta | Enviada / Aceita / Recusada |
| Notas | Observacoes |

---

## 3. MATERIAIS DE APOIO

### 3.1 Checklist de Saude Financeira (Material de Valor)

**Titulo:** Checklist Mensal de Saude Financeira para Oticas

**Conteudo:**

```
CHECKLIST MENSAL DE SAUDE FINANCEIRA
Para Oticas | WFinance

Marque o que voce faz todo mes:

FLUXO DE CAIXA
[ ] Sei exatamente quanto tenho no banco hoje
[ ] Atualizo entradas e saidas pelo menos 1x por semana
[ ] Tenho previsao de caixa para os proximos 30 dias

CONTAS A PAGAR
[ ] Sei todas as contas que vencem essa semana
[ ] Pago fornecedores em dia (sem atraso ou susto)
[ ] Tenho controle de boletos e vencimentos

CONTAS A RECEBER
[ ] Sei quanto tenho de crediario em aberto
[ ] Acompanho inadimplencia (clientes atrasados)
[ ] Faco cobrança ativa de atrasados

CONCILIACAO
[ ] Confiro extrato bancario pelo menos 1x por semana
[ ] Identifico todas as movimentacoes do extrato
[ ] Nao misturo conta PJ com conta pessoal

RESULTADOS
[ ] Sei a margem de lucro do mes passado
[ ] Sei quais produtos dao mais lucro
[ ] Confiro comissoes de vendedores

---

RESULTADO:

12-15 marcados: Parabens! Seu financeiro esta saudavel.
8-11 marcados: Atencao. Alguns pontos precisam de melhoria.
4-7 marcados: Alerta. Voce pode estar perdendo dinheiro.
0-3 marcados: Urgente. Seu financeiro precisa de ajuda.

---

Quer ajuda para organizar o financeiro da sua otica?
Faco um diagnostico gratuito de 30 minutos.

Andre Paiva | WFinance
[Instagram] [WhatsApp]
```

### 3.2 Bio Instagram WFinance

```
WFinance | Gestao Financeira Inteligente
Cuido do financeiro pra voce focar no negocio.
Fluxo de caixa | Conciliacao | Relatorios
Maceio/AL
[Link para WhatsApp ou Calendly]
```

### 3.3 Bio LinkedIn Andre

```
Fundador da WFinance | Gestao Financeira para PMEs

Ajudo donos de negocios a parar de apagar incendio no financeiro.

O que faco:
- Fluxo de caixa sempre atualizado
- Conciliacao bancaria automatica
- Relatorios semanais claros
- Controle de inadimplencia

Tecnologia + Metodo = Tranquilidade financeira.

Maceio/AL | Especializado em varejo
```

---

## 4. CALENDARIO JANEIRO 2026

### Semana 1: Infraestrutura (12-18 jan) - EMBARCADO

| Dia | Data | Tarefa Principal | Tempo | Entrega |
|-----|------|------------------|-------|---------|
| Dom | 12/jan | Limpar base de leads antiga | 2h | Base zerada |
| Seg | 13/jan | Rodar discovery novo | 2h | Nova base T1 |
| Seg | 13/jan | Extrair Top 20 T1 | 1h | Lista pronta |
| Ter | 14/jan | Mapear Instagram dos 20 | 1h | Planilha |
| Ter | 14/jan | Criar planilha de tracking | 30min | Google Sheets |
| Qua | 15/jan | Seguir 10 perfis + curtir | 30min | 10 seguidos |
| Qui | 16/jan | Seguir mais 10 + curtir | 30min | 20 seguidos |
| Sex | 17/jan | Interagir stories | 15min | Engajamento |
| Sab | 18/jan | Revisar quem seguiu de volta | 15min | Lista atualizada |

### Semana 2: Contato (19-25 jan) - EMBARCADO ate 22, depois MACEIO

| Dia | Data | Tarefa Principal | Tempo | Entrega |
|-----|------|------------------|-------|---------|
| Dom | 19/jan | Enviar 5 DMs (top engajamento) | 30min | 5 DMs |
| Seg | 20/jan | Enviar 5 DMs | 30min | 10 DMs |
| Seg | 20/jan | Criar/otimizar LinkedIn | 1h | Perfil ok |
| Ter | 21/jan | Enviar 5 DMs + criar material valor | 1h | 15 DMs + PDF |
| Qua | 22/jan | Preparar pitch + roteiro visitas | 1h | Pitch decorado |
| Qui | 23/jan | 3 visitas presenciais | 3h | 3 contatos |
| Sex | 24/jan | 2 visitas + follow-up DMs | 3h | 5 contatos total |
| Sab | 25/jan | Revisar semana, ajustar | 30min | Plano ajustado |

### Semana 3: Conversao (26-31 jan) - MACEIO

| Dia | Data | Tarefa Principal | Tempo | Entrega |
|-----|------|------------------|-------|---------|
| Dom | 26/jan | Descanso / preparar semana | - | - |
| Seg | 27/jan | 3 visitas novas | 3h | 8 contatos total |
| Ter | 28/jan | 2 visitas + follow-up quentes | 3h | 10 contatos |
| Qua | 29/jan | Diagnosticos agendados | 2h | 1-2 diagnosticos |
| Qui | 30/jan | Continuar diagnosticos | 2h | 2-3 diagnosticos |
| Sex | 31/jan | Enviar propostas | 2h | 1-2 propostas |

---

## 5. METAS E METRICAS

### 5.1 Metas Janeiro

| Indicador | Meta | Como medir |
|-----------|------|------------|
| Leads T1 limpos | 20 | Azure + Planilha |
| Perfis seguidos | 20 | Instagram |
| DMs enviadas | 15 | Planilha |
| Respostas positivas | 5 | Planilha |
| Visitas realizadas | 10 | Planilha |
| Diagnosticos | 3-4 | Planilha |
| Propostas | 2-3 | Planilha |
| **Clientes fechados** | 1 | Contrato |

### 5.2 Funil Esperado

```
20 leads selecionados
    │
    ▼ (75% tem Instagram)
15 DMs enviadas
    │
    ▼ (33% responde positivo)
5 respostas positivas
    │
    ▼ (+ visitas frias)
10 contatos totais
    │
    ▼ (30-40% aceita diagnostico)
3-4 diagnosticos
    │
    ▼ (50-70% recebe proposta)
2-3 propostas
    │
    ▼ (30-50% fecha)
1 cliente
```

### 5.3 Checkpoint Semanal

**Todo domingo, revisar:**
- [ ] Quantos perfis segui?
- [ ] Quantas DMs enviei?
- [ ] Quantas respostas recebi?
- [ ] Quantas visitas fiz?
- [ ] Quantos diagnosticos agendei?
- [ ] O que funcionou essa semana?
- [ ] O que preciso ajustar?

---

## 6. ONDE EXPLORAR MAIS

### 6.1 Expansao de Canais (Fevereiro+)

| Canal | Quando testar | Por que |
|-------|---------------|---------|
| **WhatsApp Business** | Apos 2-3 clientes | Escala o atendimento |
| **Google Meu Negocio** | Fev | Autoridade local |
| **Parcerias contadores** | Mar | Indicacoes qualificadas |
| **Eventos setor otico** | Quando tiver | Networking presencial |

### 6.2 Automacoes Futuras

| Automacao | Quando | Beneficio |
|-----------|--------|-----------|
| WhatsApp API | Apos validar processo | Envio em escala |
| Email marketing | Apos ter lista | Nurturing automatico |
| CRM integrado | Apos HubSpot ok | Pipeline automatico |
| Agendamento online | Apos volume | Menos fricção |

### 6.3 Conteudo para Autoridade

**Instagram WFinance (depois de 2-3 clientes):**
- Posts educativos: "3 erros financeiros de oticas"
- Cases anonimizados: "Como ajudei uma otica a..."
- Bastidores: "Um dia na gestao financeira"
- Dicas rapidas: Reels de 30 seg

**LinkedIn Andre:**
- Artigos sobre gestao financeira PME
- Reflexoes de empreendedorismo
- Resultados (apos ter clientes)

### 6.4 Segmentos Adjacentes (Apos dominar oticas)

| Segmento | Por que | Quando |
|----------|---------|--------|
| Clinicas odontologicas | Estrutura similar, crediario | Q2/2026 |
| Pet shops | Varejo local, mesmas dores | Q3/2026 |
| Farmacias pequenas | Volume, margem apertada | Q3/2026 |
| Lojas de roupas | Crediario, estoque | Q4/2026 |

---

## 7. RISCOS E CONTINGENCIAS

| Risco | Probabilidade | Impacto | Contingencia |
|-------|---------------|---------|--------------|
| Ninguem responde DM | Media | Alto | Focar em visitas presenciais |
| Visitas sem resultado | Media | Alto | Ajustar pitch, testar horarios |
| Objecao de preco | Alta | Medio | Focar no valor, oferecer trial |
| Concorrente local | Baixa | Medio | Diferenciar por tecnologia |
| Falta de tempo | Media | Alto | Priorizar menos leads, mais qualidade |

---

## 8. DEFINICOES IMPORTANTES

### 8.1 O Que E Sucesso em Janeiro

**Minimo aceitavel:**
- 1 cliente fechado OU 2 propostas enviadas

**Bom:**
- 1 cliente fechado + 2 diagnosticos em andamento

**Excelente:**
- 2 clientes fechados

### 8.2 Criterios de Qualificacao

**Lead qualificado para visita:**
- Otica real (nao franquia grande)
- Maceio ou regiao proxima
- Rating Google 4.0+
- Tem Instagram ativo

**Lead qualificado para diagnostico:**
- Respondeu positivo (DM ou visita)
- Demonstrou interesse real
- Tomador de decisao identificado

**Lead qualificado para proposta:**
- Fez diagnostico
- Tem dor clara identificada
- Capacidade de pagar (estimativa)

---

## 9. PROXIMOS PASSOS IMEDIATOS

### Hoje (12/jan):
- [ ] Limpar base de leads no Azure
- [ ] Ajustar criterios do discovery
- [ ] Rodar discovery novo

### Amanha (13/jan):
- [ ] Extrair Top 20 T1
- [ ] Comecar a mapear Instagram

### Essa semana:
- [ ] Criar planilha de tracking
- [ ] Seguir 20 perfis
- [ ] Preparar material de valor

---

*Documento criado: 12/01/2026*
*Proxima revisao: 19/01/2026*
*Responsavel: Andre Paiva + Consultor*
