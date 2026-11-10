# 🤝 AGENT HANDOFF: Mentor & Guia do curso.dev

> **Atenção para o Agente de IA (Antigravity / Assistente):**
> Você está atuando como **Mentor e Guia de Aprendizado** do desenvolvedor **Guilherme** no **curso.dev** (do Filipe Deschamps), desenvolvendo o projeto **`clone-tabnews`**.
>
> **LEIA ESTE ARQUIVO COM ATENÇÃO ANTES DE RESPONDER.**
> Ele contém a identidade do seu papel, o histórico completo do que já foi feito, as decisões arquiteturais tomadas e a próxima tarefa a ser executada. Ao final de cada sessão, atualize o bloco de *Notas de Sessão* para manter a continuidade perfeita entre o computador de casa e o do estágio.

---

## 🎯 1. Princípios de Atuação (Seu Papel como Tutor)

1. **Entendimento antes da execução:**
   - Nunca cuspa códigos prontos gigantescos sem explicar o conceito.
   - O Guilherme precisa entender os fundamentos (arquitetura, porquês e decisões de design).
2. **O Guilherme no comando:**
   - Ele escreve, digita os comandos e gerencia o repositório. Você orienta passo a passo, aponta o caminho e explica o que cada instrução faz.
3. **Dissecar e aprender com erros:**
   - Quando um erro aparecer, não apenas dê a correção; explique de onde o erro veio, o que a mensagem significa e por que a solução funciona.
4. **Padrão profissional:**
   - Commits atômicos, descritivos e no padrão Conventional Commits (ex: `feat: ...`, `fix: ...`).
   - Respeito à didática do curso.dev (evitar atalhos mágicos como `create-next-app` — construir do zero para aprender).

---

## 💻 2. Contexto do Ambiente de Desenvolvimento

- **Sistema Operacional:** Windows 11 com **WSL 2 (Ubuntu)**.
- **Local do Projeto no Linux:** `/home/guilherme/clone-tabnews` (armazenado no filesystem nativo do Linux no WSL para máxima performance de I/O).
- **Docker:** **Docker Engine nativo no Ubuntu** (sem Docker Desktop pesado), configurado para rodar sem `sudo` (`sudo usermod -aG docker $USER`).
- **Node & NVM:** NVM instalado no Ubuntu (`v0.40.1`), Node.js LTS (`v26.13.0`) e npm configurados.
- **Editor:** Visual Studio Code no Windows conectado ao WSL via extensão oficial (`ms-vscode-remote.remote-wsl`).
- **Git & GitHub:**
  - Repositório remoto: `https://github.com/GuilhermeSilva-25/clone-tabnews.git`
  - Conexão configurada via **HTTPS com Git Credential Manager** (`/mnt/c/Program Files/Git/mingw64/bin/git-credential-manager.exe`).
  - *Nota importante:* Na máquina do estágio a porta 22 (SSH) estava bloqueada pela rede, por isso o HTTPS com GCM foi adotado como padrão estável.

---

## 🗺️ 3. Status da Jornada (Roadmap do curso.dev)

| Módulo | Descrição | Status |
| :--- | :--- | :--- |
| **01. Ambiente Local** | WSL 2, Ubuntu, Docker Engine nativo, NVM, Node LTS, Git | ✅ **Concluído** |
| **02. Setup do Projeto** | `npm init -y`, `package.json`, Next.js do zero, `.gitignore` | ✅ **Concluído** |
| **03. Primeira Página** | `pages/index.js`, Fast Refresh no `http://localhost:3000` | ✅ **Concluído** (commit `932fd2f`) |
| **04. Deploy Contínuo** | Configuração e deploy na **Vercel** | ⏳ **PRÓXIMO PASSO** |
| **05. Banco de Dados** | Docker Compose com PostgreSQL local | ⏳ Pendente |
| **06. Migrations** | `node-pg-migrate` e modelagem | ⏳ Pendente |
| **07. Testes Automatizados** | Jest, orquestração e GitHub Actions | ⏳ Pendente |
| **08. Core do TabNews** | APIs, autenticação, posts e frontend completo | ⏳ Pendente |

---

## 🐛 4. Diário de Decisões e Gotchas Resolvidos

1. **Conflito de formato de módulo (CommonJS vs ESM):**
   - *Problema:* O `npm init -y` do Node v26 gerou `"type": "commonjs"` automaticamente no `package.json`. Ao rodar `pages/index.js` com `export default Home`, o Turbopack do Next.js quebrou acusando conflito de módulo.
   - *Solução:* Removemos as chaves `"type": "commonjs"` e `"main": "index.js"` do `package.json`, permitindo que o Next.js gerencie os módulos nativamente.
2. **Bloqueio de SSH (Porta 22):**
   - *Problema:* O comando `ssh -T git@github.com` congelava no estágio devido a bloqueio de firewall na porta 22.
   - *Solução:* Configuramos o Git Credential Manager sobre HTTPS. Rápido, seguro e funciona em qualquer rede.
3. **Local dos arquivos:**
   - O repositório foi clonado dentro da home do Ubuntu (`~/clone-tabnews`) para garantir que o Next.js e o Docker rodem com velocidade nativa (evitando a lentidão da ponte 9P em `/mnt/c/`).

---

## 📝 5. Diário de Bordo (Session Handoff Log)

### Sessão 01 — 10/11/2026 (Máquina: Estágio)
- **Tutor:** Antigravity (Sessão inicial)
- **O que foi feito:**
  - Instalação e ativação do WSL 2 e distribuição Ubuntu.
  - Instalação do Docker Engine e Docker Compose nativos no Linux.
  - Configuração do NVM e Node LTS.
  - Instalação da extensão WSL no VS Code.
  - Inicialização do projeto Next.js do zero com `package.json` limpo e `.gitignore` protegido (`node_modules`, `.next`).
  - Criação da primeira rota `pages/index.js` renderizando no navegador.
  - Primeiro commit profissional realizado e sincronizado no GitHub (`feat: adiciona Next.js e cria primeira pagina`).
- **Próxima Ação Imediata (para o tutor de casa):**
  - O Guilherme vai abrir o projeto no PC de casa.
  - Se a máquina de casa ainda não tiver WSL/Node/Docker, auxiliá-lo a clonar e configurar o ambiente. Se já tiver, apenas dar `git pull`.
  - Iniciar a aula de **Deploy na Vercel** (conectar o repositório GitHub à Vercel para publicação automática a cada push).

---
*(Próximo agente: adicione a "Sessão 02" abaixo ao encerrar sua jornada em casa!)*
