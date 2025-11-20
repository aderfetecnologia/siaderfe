# 🏛️ SIADERFE — Sistema de Administração e Gestão

O **SIADERFE** é um sistema completo para administração institucional, gestão de unidades, membros, finanças e módulos adicionais.  
O projeto foi criado com foco em **escalabilidade**, **boas práticas**, **segurança**, **arquiteturas modernas** e migração progressiva do monolito para uma estrutura distribuída.

---

# 🚀 Objetivo do Sistema

O sistema tem por objetivo:

- Centralizar informações administrativas  
- Gerenciar membros, departamentos e unidades  
- Controlar financeiro, relatórios e permissões  
- Integrar versões **desktop (Java)**, **web (Next.js)** e **mobile (React Native)**  
- Evoluir de um **monolito** para uma arquitetura **modular/distribuída**  

---

# 🧰 Tecnologias Utilizadas

### **Backend / Core**
- Java  
- Spring  
- MySQL  
- Docker / Kubernetes  

### **Frontend**
- JavaFX (desktop)  
- Next.js / React (web)  
- React Native (mobile)

### **Infra e DevOps**
- Docker  
- Kubernetes  
- GitHub Actions (CI/CD)  
- Observabilidade (Grafana, Prometheus)

---

# 🧱 Arquiteturas do Sistema

O projeto possui duas visões principais de arquitetura:

---

## 🟦 Arquitetura Monolítica

![Arquitetura Monolítica](docs/arquitetura_monolitica.png)

---

## 🟩 Arquitetura Distribuída (Futura / Evolutiva)

![Arquitetura Distribuída](docs/arquitetura_distribuida.png)

---

# 🪴 Migração — Strangler Fig Pattern

Para evoluir o SIADERFE de um monolito para uma arquitetura distribuída sem interrupções, adotamos o padrão **Strangler Fig**.

Este padrão permite migrar **módulo por módulo**, sem quebra, substituindo partes antigas por novas gradualmente.

### 🧩 Como funciona a migração

1. **Identificar módulo** no monolito (membros, financeiro, relatórios etc.)  
2. Criar **novo serviço** para este módulo  
3. Implementar **API Gateway** para rotear chamadas  
4. Ativar módulo novo usando **feature flags**  
5. Migrar dados usando **CDC / dual-write** quando necessário  
6. Desativar o módulo antigo do monolito  
7. Remover código obsoleto  
8. Repetir para o próximo módulo

---

## 🔀 Fluxo (Strangler Fig)

