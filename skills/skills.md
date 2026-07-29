---
name: skills-experiencia
description: "Record of completed tasks and workflows to guide new implementations in the project."
---

# Experience History and Workflows (Skills)

This file records the history of implementations carried out to serve as a direct reference for new developments.

---

## 1. Payload Format Update (Encryption)
* **Goal:** Synchronize changes in the encryption format (AES-GCM) between Backend (Python/Flask) and Frontend (Vite/React).
* **Steps executed:**
  1. Changed `TransitCipher.encrypt()` in the backend to return `{iv, data, version}`.
  2. Maintained `encrypt_to_base64_legacy()` for backward compatibility.
  3. Updated `decryptPayload` in the frontend to handle the new JSON object.
  4. Implemented `base64ToUint8Array` converter on the client and automatic fallback.
* **Files:** `backend/app.py`, `src/services/apiClient.js`

## 2. External API Integration (Other Services)
* **Goal:** Establish secure communication between the TwistAudio backend and third-party services (e.g., Clerk Auth or Media Streams).
* **Steps executed:**
  1. Created isolated HTTP request service with error handling.
  2. Implemented `X-App-Client: TwistAudio` header for internal validation.
  3. Added strict timeout and automatic retry flow to avoid bottlenecks.
  4. Mapped private keys exclusively through the secrets file (.env).
* **Files:** `backend/stream_token_service.py`, `backend/secrets/.env`

## 3. Implementation of Secure Cookies and CSRF
* **Goal:** Migrate authentication storage from LocalStorage to httpOnly cookies and enable SameSite protection.
* **Steps executed:**
  1. Added `session_id` and `csrf_token` cookies on login.
  2. Enabled flags `httponly=True`, `secure=True` (in production), and `samesite='Strict'`.
  3. Removed local storage in the frontend and temporary in-memory variables.
  4. Configured `@require_auth` decorator in the backend validating cookies and CSRF.
* **Files:** `backend/app.py`, `src/services/apiClient.js`

---

## How to Use
1. Before starting any task corresponding to these topics, consult this file to replicate the established logic, architecture, and conventions.
2. When creating new complex workflows, record them in this file using the same format.
