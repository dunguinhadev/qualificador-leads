# Qualificador Inteligente de Leads — Lei 14.300 (GD)

Pipeline de automação para triagem, validação regulatória e qualificação comercial de leads interessados em energia solar e geração distribuída (Lei Federal nº 14.300/2022), utilizando regras de negócio e modelos de linguagem (LLMs).

## Problema de Negócio

Na operação comercial de projetos fotovoltaicos e gestão de créditos de energia, equipes de pré-vendas gastam horas analisando faturas manualmente para responder três perguntas básicas antes de acionar um consultor:

1. O consumo médio mensal em kWh torna a operação financeiramente viável?
2. O perfil do consumidor (residencial, comercial ou rural) e o grupo tarifário (Grupo B ou Grupo A) se enquadram nas regras vigentes da Lei 14.300?
3. Qual é a prioridade comercial desse lead para o time de vendas?

Este projeto automatiza essa triagem recebendo os dados do lead, aplicando regras de elegibilidade regulatória e utilizando um agente de IA para classificar a maturidade comercial e gerar uma abordagem inicial personalizada.

## Arquitetura do Fluxo

```text
[Base de Leads / Formulário]
        │
        ▼
[1. Validação e Padronização]
   • Normaliza consumo (kWh), distribuidora e tipo de ligação
        │
        ▼
[2. Motor de Regras — Lei 14.300]
   • Filtra consumo mínimo viável (a partir de 350 kWh/mês)
   • Classifica modalidade (Autoconsumo Local, Remoto ou Geração Compartilhada)
        │
        ▼
[3. Agente Qualificador (LLM via API)]
   • Avalia perfil, urgência e potencial de economia
   • Retorna saída estruturada (score, temperatura e gancho comercial)
        │
        ▼
[Saída Qualificada] ──► Integração via webhook (n8n / CRM / WhatsApp)
