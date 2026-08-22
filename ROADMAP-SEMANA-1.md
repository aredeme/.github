# Roadmap Semana 1 — Sair da Fábrica de Sistemas

**Objetivo:** Reduzir burocracia 10x e começar a codificar o "primeiro sistema real" sexta-feira 18:00.

**Princípio:** Implementação paralela com processo (não sequencial). Testes/mocks ANTES de revisão.

---

## 🔥 SEGUNDA-FEIRA 09:00 — Começar agora

### ✅ Issue #55: CODER-GH-ACCESS-01 — Validar acesso arede-system
- **Tempo:** 30 min
- **Prioridade:** 🔴 CRÍTICO
- **Outcome:** Acesso comprovado ou diagnóstico claro

**Checklist:**
```
- [ ] git clone https://github.com/aredeme/arede-system no workspace Coder
  ✓ Se funcionar → CLOSE issue
  ✗ Se 403 → Capturar stderr, abrir diagnóstico sem Gate
- [ ] Validar: repository existe e está privado
- [ ] Usar credentials da sessão Coder
```

**Aceite:**
- Clone bem-sucedido OU diagnóstico técnico documentado

---

### ✅ Issue #26: GITHUB-MCP-OPS-02 — Conector GitHub bot governado
- **Tempo:** 6h (não sequencial com #55)
- **Prioridade:** 🔴 CRÍTICO
- **Outcome:** Bot 70% implementado com mocks, testes passando

**Checklist:**
```
- [ ] Implementar allowlist de campos editáveis (title, body, assignees, labels, milestone)
  - Implementar teste: campos que NÃO podem ser editados devem falhar fechado
- [ ] Implementar testes unitários (mocks GraphQL, sem GitHub real)
  - Cobertura: ambiguidade de field name → erro específico
  - Cobertura: opção não existe → erro específico
- [ ] Validar: nenhum GraphQL arbitrário escapa
- [ ] Validar: sem retry cego de mutação (timeout = parada, sem retry automático)
- [ ] Commit: "feat: GitHub MCP conector com allowlist, testes mocks"
```

**Aceite:**
- Testes locais passando 100%
- Nenhuma chamada real a GitHub (mocks apenas)
- Implementação pronta para plugar GitHub App real quinta-feira

---

### ✅ Issue #45: Sincronizar docs PADRÃO-GERAL-001
- **Tempo:** 2h
- **Prioridade:** 🟠 ALTO
- **Outcome:** GitHub Action rodando todos os dias, sem trabalho manual

**Checklist:**
```
- [ ] Criar .github/workflows/sync-padrão-001.yml
  - Trigger: diariamente 06:00 + manual (workflow_dispatch)
  - Clone repo docs canônico
  - rsync PADRÃO-GERAL-001 → arede-infra/, arede-mcp/, arede-work-controller/
  - Valida hash de integridade
  - Commit automático com autor "arede-automation"
  - Abre PR automático
- [ ] Testar: execução manual do workflow
- [ ] Validar: arquivo foi sincronizado corretamente
```

**Aceite:**
- Action executa sem erro
- Documento sincronizado em 3 repos
- PR automático aberto

---

### ✅ Issue #56: CODER-TOOLING-01 — Dockerfile + CI automático
- **Tempo:** 3h
- **Prioridade:** 🟠 ALTO
- **Outcome:** Tooling validada via CI, sem 5 gates sequenciais

**Checklist:**
```
- [ ] Criar/atualizar Dockerfile
  - Instala: Claude Code CLI (versionado), Codex CLI (versionado)
  - Instala VSCode extensions: anthropic.claude-code, openai.chatgpt
  - Valida: nenhum token/secret embutido
  - Valida: todas as ferramentas presentes
- [ ] Criar .github/workflows/validate-tooling.yml
  - Build Dockerfile
  - Spin workspace teste descartável
  - Valida: presença/versão de ferramentas
  - Valida: sem secret no output
- [ ] Testar: workflow passa localmente
- [ ] REMOVER: Gates 2, 3, 4, 5 do Project (substituir por CI automático)
```

**Aceite:**
- Workflow passa 100%
- Dockerfile válido
- CI roda em cada commit

---

### ✅ Issue #42: SEC-TRUST-01 — Fase 1 Google Cloud (diagnóstico)
- **Tempo:** 1h (planejamento, não implementação)
- **Prioridade:** 🟠 ALTO
- **Outcome:** Escopo de "fase 1 mínima" aprovado

**Checklist:**
```
- [ ] Documentar: "Qual é o mínimo viável para Workload Identity Federation?"
  - Um único role (somente-leitura) no Secret Manager
  - Coder workspace como identity
  - Reversibilidade: como remover em 15 min se quebrar?
- [ ] Compartilhar com revisor independente
- [ ] Aguardar aprovação quinta-feira
```

**Aceite:**
- Escopo documentado
- Reversibilidade comprovada
- Aprovado por revisor independente

---

## 📅 TERÇA-FEIRA 10:00 — Revisão rápida

**Revisor independente:**
- [ ] Revisa #26 (mocks + testes)
- [ ] Revisa #45 (GitHub Action)
- [ ] Revisa #56 (Dockerfile + CI)
- [ ] Aprova ou redireciona (max 2h)

---

## 📅 QUINTA-FEIRA 14:00 — Gates de segurança

**Gate [H] — Aprova:**
- [ ] #26: GitHub App permission (conector bot)
- [ ] #42: Google Cloud IAM config (fase 1 mínima)

---

## 🚀 SEXTA-FEIRA 09:00 — Go live

- [ ] #26: Plugar GitHub App real (já está 70% pronto)
- [ ] #26: Smoke test em dev
- [ ] #42: Deploy fase 1 Google Cloud (se Gate aprovado)

---

## 🎯 SEXTA-FEIRA 18:00 — Resultado final

✅ Acesso arede-system confirmado  
✅ Bot conector live em dev (70% funcional)  
✅ Sync docs automático (rodando)  
✅ Tooling CI validada  
✅ Google Cloud IAM fase 1 (aprovado/planejado)  
🚀 **FND-03...FND-07 liberadas para codificar segunda-feira**  

---

## ⏸️ O que PAUSAR até sexta-feira 18:00

Issues: #3, #5, #6, #8, #9, #10, #11, #12 (FND-XX, Features, Initiative)

**Razão:** Bloqueadas por #55 (acesso) + #26 (conector) + #42 (trust).

**Status:** Marked as `blocked` no Project.

**Liberar:** Sexta-feira 18:00 quando #55 estiver OK.

---

## 📱 Mobile-first notes

- Todos os scripts (#45, #56, #26-mocks) rodam via bash/Python/Docker
- GitHub Actions = serverless, sem desktop
- Revisão = GitHub web (mobile-friendly)
- Codificação real (FND-03+) sai do Coder quando #55 OK

---

## Próximos passos

1. **Segunda-feira 09:00:** Abrir este documento + Project #2
2. **Para cada issue:** Seguir checklist exatamente como está
3. **Terça 10:00:** Revisor independente aprova ou redireciona
4. **Sexta 18:00:** Você sai da fábrica

**Good luck. Você consegue.**
