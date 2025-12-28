# MCP Tools v2 - Documento de Trabalho

## Índice
1. [Visão Geral](#1-visão-geral)
2. [Requisitos Funcionais](#2-requisitos-funcionais)
3. [Requisitos Não-Funcionais](#3-requisitos-não-funcionais)
4. [Casos de Uso](#4-casos-de-uso)
5. [Especificação Técnica](#5-especificação-técnica)
6. [Diagramas](#6-diagramas)
7. [Histórico de Decisões](#7-histórico-de-decisões)
8. [Pendências](#8-pendências)

---

## 1. Visão Geral

### 1.1 Contexto

Este é um **projeto piloto** para validar o ambiente de colaboração entre IAs. 
O projeto principal (DLL Nelogica, Ringbuffer, trading) será iniciado após a 
estruturação deste ambiente.

### 1.2 Objetivo

Expandir o MCP Server atual (mcp-github-writer-2) com novas tools para 
gerenciamento completo do repositório GitHub.

### 1.3 Escopo

**O que faz (IN):**
- Deletar arquivos do repositório
- Listar histórico de commits (geral e por arquivo)
- Ver detalhes de um commit específico
- Listar branches existentes
- Criar novas branches
- Alternar branch de trabalho

**O que NÃO faz (OUT):**
- Merge de branches (complexidade alta, risco de conflitos)
- Reverter commits (operação destrutiva)
- Gerenciar Pull Requests
- Gerenciar Issues

### 1.4 Tools Atuais (v1)

| Tool | Função |
|------|--------|
| `list_files` | Lista arquivos de um diretório |
| `read_file` | Lê conteúdo de um arquivo |
| `write_file` | Cria ou atualiza arquivo (com commit) |

### 1.5 Tools Propostas (v2)

| Tool | Função | Prioridade |
|------|--------|------------|
| `delete_file` | Remove arquivo (com commit) | Alta |
| `list_commits` | Lista histórico de commits | Alta |
| `get_commit` | Detalhes de um commit | Média |
| `list_branches` | Lista branches | Média |
| `create_branch` | Cria nova branch | Média |
| `switch_branch` | Muda branch ativa | Média |

### 1.6 Benefícios para o Projeto Principal

Ao concluir este piloto, o ambiente estará pronto para:
- Documentar e desenvolver o projeto DLL Nelogica/Ringbuffer
- Gerenciar versões com histórico completo
- Permitir revisão colaborativa entre IAs
- Trabalhar com branches para features isoladas

---

## 2. Requisitos Funcionais

*[A ser definido]*

---

## 3. Requisitos Não-Funcionais

*[A ser definido]*

---

## 4. Casos de Uso

*[A ser definido]*

---

## 5. Especificação Técnica

*[A ser definido]*

---

## 6. Diagramas

*[A ser definido]*

---

## 7. Histórico de Decisões

| Data | Decisão | Justificativa |
|------|---------|---------------|
| 2024-12-28 | Adotar documento único de trabalho | Evitar dispersão de informação em múltiplos arquivos |
| 2024-12-28 | MCP Tools v2 como projeto piloto | Validar ambiente antes do projeto principal (Nelogica) |

---

## 8. Pendências

- [x] Definir escopo do projeto MCP Tools v2
- [ ] Levantar requisitos funcionais
- [ ] Levantar requisitos não-funcionais
- [ ] Definir casos de uso
- [ ] Especificar tecnicamente cada tool

---

*Última atualização: 2024-12-28*
