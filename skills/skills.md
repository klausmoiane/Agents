---
name: skills-experiencia
description: "Registro de tarefas concluídas e fluxos de trabalho para guiar novas implementações no projeto."
---

# Histórico de Experiência e Workflows (Skills)

Este arquivo registra o histórico de implementações realizadas para servir de referência direta em novos desenvolvimentos.

---

## 1. Atualização do Formato de Payload (Criptografia)
* **Objetivo:** Sincronizar modificações no formato de encriptação (AES-GCM) entre Backend (Python/Flask) e Frontend (Vite/React).
* **Passos executados:**
  1. Alterado `TransitCipher.encrypt()` no backend para retornar `{iv, data, version}`.
  2. Mantido `encrypt_to_base64_legacy()` para retrocompatibilidade.
  3. Atualizado `decryptPayload` no frontend para lidar com o novo objeto JSON.
  4. Implementado conversor `base64ToUint8Array` no cliente e fallback automático.
* **Arquivos:** `backend/app.py`, `src/services/apiClient.js`

## 2. Integração de API Externa (Outros Serviços)
* **Objetivo:** Estabelecer comunicação segura entre o backend TwistAudio e serviços de terceiros (ex: Clerk Auth ou Streams de Mídia).
* **Passos executados:**
  1. Criado serviço de requisição HTTP isolado com tratamento de erros.
  2. Implementado cabeçalho `X-App-Client: TwistAudio` para validação interna.
  3. Adicionado timeout rígido e fluxo de retry automático para evitar gargalos.
  4. Mapeado chaves privadas exclusivamente através do arquivo de segredos (.env).
* **Arquivos:** `backend/stream_token_service.py`, `backend/secrets/.env`

## 3. Implementação de Cookies Seguros e CSRF
* **Objetivo:** Migrar armazenamento de autenticação do LocalStorage para cookies httpOnly e habilitar proteção SameSite.
* **Passos executados:**
  1. Adicionado cookies `session_id` e `csrf_token` no login.
  2. Habilitado flags `httponly=True`, `secure=True` (em produção) e `samesite='Strict'`.
  3. Removido armazenamento local no frontend e variáveis temporárias em memória.
  4. Configurado decorator `@require_auth` no backend validando cookies e CSRF.
* **Arquivos:** `backend/app.py`, `src/services/apiClient.js`

---

## Como Usar
1. Antes de iniciar qualquer tarefa correspondente a estes tópicos, consulte este arquivo para replicar a lógica, arquitetura e convenções estabelecidas.
2. Ao criar novos fluxos complexos, registre-os neste arquivo no mesmo formato.
