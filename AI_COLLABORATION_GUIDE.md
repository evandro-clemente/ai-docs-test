# Guia de Colaboração entre IAs

## 📋 Índice

1. [Visão Geral](#1-visão-geral)
2. [Participantes e Papéis](#2-participantes-e-papéis)
3. [Fluxo de Trabalho](#3-fluxo-de-trabalho)
4. [Regras de Operação](#4-regras-de-operação)
5. [Estrutura do Repositório](#5-estrutura-do-repositório)
6. [Versionamento](#6-versionamento)
7. [Formato de Revisão](#7-formato-de-revisão)
8. [Resolução de Conflitos](#8-resolução-de-conflitos)

---

## 1. Visão Geral

### 1.1 Propósito

Este repositório é um **workspace colaborativo** onde múltiplas IAs trabalham juntas, sob supervisão humana, para criar e revisar documentação técnica e código.

### 1.2 Princípios

- **Documentar antes de codificar** - Toda implementação é precedida de documentação
- **Iterações curtas** - Foco na fase atual, não em detalhes de fases futuras
- **Versionamento completo** - Toda alteração gera um commit (histórico preservado)
- **Decisão humana** - O humano é o árbitro final em qualquer conflito

### 1.3 Metodologia

Inspirada em métodos ágeis:
- Requisitos macro primeiro, detalhes conforme necessidade
- Documentação da fase atual sempre atualizada
- Facilitar reescrita e adaptação futura através de docs claros

---

## 2. Participantes e Papéis

### 2.1 Humano Árbitro

**Quem**: Evandro (dono do repositório)

**Responsabilidades**:
- Definir objetivos e prioridades
- Arbitrar conflitos entre IAs
- Aprovar ou rejeitar sugestões
- Decidir quando uma fase está concluída
- Transportar informações entre IAs quando necessário

**Autoridade**: Palavra final em qualquer decisão

---

### 2.2 IA Autora (Claude)

**Função**: Única IA com **permissão de escrita** no repositório

**Responsabilidades**:
- Criar e editar documentos
- Implementar código
- Gerenciar estrutura do repositório
- Executar alterações solicitadas pelo Árbitro
- Incorporar feedback das IAs Revisoras (após aprovação do Árbitro)

**Permissões**:
- ✅ Criar arquivos
- ✅ Editar arquivos
- ✅ Deletar arquivos
- ✅ Listar estrutura
- ✅ Ler conteúdo

**Restrições**:
- ❌ Não implementa código sem documentação prévia aprovada
- ❌ Não ignora feedback de revisores sem aprovação do Árbitro

---

### 2.3 IAs Revisoras (ChatGPT, Gemini, outras)

**Função**: Revisar, analisar e sugerir melhorias

**Responsabilidades**:
- Ler documentos do repositório
- Analisar clareza, completude e precisão
- Identificar erros, inconsistências e gaps
- Sugerir melhorias estruturais e de conteúdo
- Propor código (que será passado ao Claude via Árbitro)

**Permissões**:
- ✅ Ler arquivos (via API/MCP próprio)
- ✅ Sugerir alterações (via chat com Árbitro)
- ✅ Gerar código para análise

**Restrições**:
- ❌ Não editam diretamente no repositório
- ❌ Sugestões passam pelo Árbitro antes de implementação

---

## 3. Fluxo de Trabalho

### 3.1 Diagrama Geral

```
┌─────────────────────────────────────────────────────────────────┐
│                         HUMANO ÁRBITRO                          │
│                    (decide, prioriza, aprova)                   │
└─────────────────────────────────────────────────────────────────┘
         │                      │                      │
         ▼                      ▼                      ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   IA AUTORA     │    │  IA REVISORA 1  │    │  IA REVISORA 2  │
│   (Claude)      │    │  (ChatGPT)      │    │  (Gemini)       │
│                 │    │                 │    │                 │
│  • Escreve      │    │  • Lê           │    │  • Lê           │
│  • Implementa   │    │  • Revisa       │    │  • Revisa       │
│  • Versiona     │    │  • Sugere       │    │  • Sugere       │
└────────┬────────┘    └────────┬────────┘    └────────┬────────┘
         │                      │                      │
         ▼                      ▼                      ▼
┌─────────────────────────────────────────────────────────────────┐
│                           GITHUB                                │
│                    (repositório versionado)                     │
│                                                                 │
│  • Armazena documentos e código                                 │
│  • Mantém histórico completo de alterações                      │
│  • Cada commit = uma versão preservada                          │
└─────────────────────────────────────────────────────────────────┘
```

### 3.2 Ciclo de Iteração

```
1. ÁRBITRO define objetivo
         │
         ▼
2. CLAUDE documenta/implementa
         │
         ▼
3. ÁRBITRO solicita revisão
         │
         ▼
4. REVISORAS analisam e comentam
         │
         ▼
5. ÁRBITRO avalia feedback
         │
         ├── Aprova sugestões ──▶ Volta ao passo 2
         │
         └── Rejeita / Finaliza ──▶ Fase concluída
```

### 3.3 Fluxo de Código (quando aplicável)

```
1. Documentar requisitos (Claude)
         │
         ▼
2. Revisar requisitos (Revisoras)
         │
         ▼
3. Aprovar documentação (Árbitro)
         │
         ▼
4. Implementar código (Claude)
         │
         ▼
5. Revisar código (Revisoras) ◄── Revisoras podem sugerir código
         │                        que Árbitro passa para Claude
         ▼
6. Aprovar implementação (Árbitro)
```

---

## 4. Regras de Operação

### 4.1 Para o Árbitro

1. Sempre fornecer contexto suficiente ao iniciar um chat com qualquer IA
2. Ao mudar de IA, resumir o estado atual do projeto
3. Decisões finais são registradas nos documentos
4. Em caso de sugestões conflitantes entre revisoras, o Árbitro decide

### 4.2 Para a IA Autora (Claude)

1. Toda alteração gera commit com mensagem descritiva
2. Não implementar código sem documentação aprovada
3. Incorporar feedback aprovado pelo Árbitro
4. Manter estrutura de pastas organizada
5. Documentar decisões técnicas tomadas

### 4.3 Para IAs Revisoras

1. Usar o formato de revisão padronizado (seção 7)
2. Ser específico nas sugestões (indicar onde e como melhorar)
3. Distinguir entre: erros, sugestões e preferências pessoais
4. Não assumir que sugestões serão implementadas automaticamente

---

## 5. Estrutura do Repositório

```
ai-docs-test/
│
├── README.md                    # Visão geral do projeto
├── AI_COLLABORATION_GUIDE.md    # Este documento
│
├── docs/                        # Documentação do projeto
│   ├── requisitos/              # Requisitos funcionais e não-funcionais
│   ├── arquitetura/             # Diagramas e decisões arquiteturais
│   ├── casos-de-uso/            # Descrição de casos de uso
│   └── guias/                   # Tutoriais e guias operacionais
│
├── src/                         # Código-fonte (quando houver)
│
└── revisoes/                    # Histórico de revisões importantes (opcional)
```

---

## 6. Versionamento

### 6.1 Como Funciona

- **Cada `write_file` = 1 commit** no GitHub
- O histórico completo fica em: `/commits/main`
- Nenhuma versão é perdida

### 6.2 Boas Práticas

| Ação | Mensagem de Commit Sugerida |
|------|----------------------------|
| Criar documento | `Cria [nome-do-doc]: [descrição breve]` |
| Atualizar documento | `Atualiza [nome-do-doc]: [o que mudou]` |
| Incorporar feedback | `Incorpora revisão: [origem do feedback]` |
| Deletar arquivo | `Remove [nome]: [motivo]` |

### 6.3 Capacidades Futuras (a implementar)

- Ver histórico de commits de um arquivo
- Comparar versões (diff)
- Trabalhar com branches (feature branches)
- Reverter para versões anteriores

---

## 7. Formato de Revisão

Toda revisão deve seguir este formato padronizado:

```markdown
## 📋 Revisão: [Nome do Documento]

**Revisor**: [Nome da IA]  
**Data**: [Data]  
**Versão revisada**: [commit ou "mais recente"]

### ✅ Pontos Positivos
- [O que está bom e deve ser mantido]

### ⚠️ Sugestões de Melhoria
1. **[Seção/Local]**: [Sugestão específica]
2. **[Seção/Local]**: [Sugestão específica]

### ❌ Problemas Encontrados
- **[Severidade: Alta/Média/Baixa]**: [Descrição do problema]

### 💡 Sugestões Adicionais
- [Ideias que agregam valor mas não são essenciais]

### 🎯 Veredicto

- [ ] ✅ Aprovado - Pronto para uso
- [ ] ⚠️ Aprovado com ressalvas - Funcional, mas pode melhorar
- [ ] ❌ Necessita revisão - Problemas que impedem aprovação
```

### 7.1 Critérios para Veredicto

| Veredicto | Quando Usar |
|-----------|-------------|
| **Aprovado** | Documento claro, completo, sem erros |
| **Aprovado com ressalvas** | Funcional, mas com melhorias sugeridas não-críticas |
| **Necessita revisão** | Erros, inconsistências ou gaps que comprometem o uso |

---

## 8. Resolução de Conflitos

### 8.1 Conflitos entre Revisoras

Quando ChatGPT e Gemini (ou outras) divergem:

1. Árbitro analisa ambos os pontos de vista
2. Árbitro pode pedir argumentação adicional
3. Árbitro decide qual seguir (ou nenhum, ou combinar)
4. Decisão é documentada no commit

### 8.2 Conflitos entre Revisora e Autora

Quando uma Revisora sugere algo que Claude discorda:

1. Claude pode expor seu contra-argumento ao Árbitro
2. Árbitro avalia ambas as perspectivas
3. Árbitro decide
4. Decisão final é implementada sem discussão adicional

### 8.3 Princípio Geral

> **O Árbitro Humano sempre tem a palavra final.**  
> IAs são consultoras; a decisão é humana.

---

## Histórico do Documento

| Versão | Data | Alteração |
|--------|------|-----------|
| 1.0 | 2024-12-28 | Criação inicial |

---

*Documento mantido por Claude (IA Autora) sob supervisão de Evandro (Árbitro)*
