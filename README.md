# 💎 Câmbio Prime — Terminal Executivo & Conversor de Moedas

Aplicação web moderna de conversor de moedas global com taxas interbancárias em tempo real e **persistência contínua de histórico no Firebase Firestore**, com autenticação anônima (sem necessidade de tela de login).

---

## 🚀 Funcionalidades

- ⚡ **Cotações em Tempo Real:** Conexão com API de taxas de câmbio comercial com atualização automática a cada 60s.
- 🔒 **Persistência no Firebase Firestore:** Todos os cálculos e conversões são gravados sob o identificador anônimo (`UID`) do usuário.
- 👤 **Autenticação Anônima (`signInAnonymously`):** Sem formulários de cadastro; identificador de sessão gerado e mantido no dispositivo.
- 📊 **Painel de Tendência e Paridade:** Gráfico vetorial interativo com máxima/mínima 24h, volume interbancário e volatilidade.
- 📜 **Auditoria & Histórico:**
  - Repetir conversão com 1 clique.
  - Baixar comprovante oficial de operação (`.txt`) com código de autenticação simulado Bacen.
  - Exportar histórico completo para planilha Excel/CSV (`.csv` com codificação UTF-8 BOM).
  - Limpar histórico sincronizado na nuvem.
- 🎨 **Design System Stitch:** Dark mode executivo com Tailwind CSS, glassmorphism e tipografia Plus Jakarta Sans / Inter.

---

## 📦 Como Publicar no GitHub Pages

### Opção 1: Upload Direto pelo Navegador (Sem Git instalado)

1. Crie um novo repositório no seu [GitHub](https://github.com/new) (ex: `cambio-prime`).
2. Clique em **"Upload an existing file"** ou arraste todos os arquivos da pasta para o repositório.
3. No seu repositório no GitHub, vá em **Settings** > **Pages** (no menu lateral esquerdo).
4. Em **Build and deployment**:
   - **Source:** Selecione `Deploy from a branch`
   - **Branch:** Escolha `main` (ou `master`) e a pasta `/(root)`.
   - Clique em **Save**.
5. Aguarde cerca de 1 a 2 minutos e acesse o link publicado! (ex: `https://seu-usuario.github.io/cambio-prime/`).

---

### Opção 2: Via Linha de Comando (Git)

```bash
# 1. Inicialize o repositório
git init
git add .
git commit -m "feat: publicando Cambio Prime no GitHub Pages"

# 2. Conecte ao seu repositório remoto (substitua com sua URL)
git remote add origin https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
git branch -M main
git push -u origin main
```

Em seguida, ative o **GitHub Pages** em **Settings > Pages > Branch: main > Save**.

---

## ⚙️ Configuração do Firebase Firestore

Para que os dados sejam salvos no seu projeto do Firebase, garanta que as **Regras do Firestore** permitam a escrita de usuários anônimos:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /conversions/{document} {
      allow read, write: if request.auth != null;
    }
  }
}
```

E no Console do Firebase (**Authentication > Sign-in method**), ative o provedor **Anônimo (Anonymous)**.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5 & Vanilla JavaScript (ES Modules)**
- **Tailwind CSS CDN**
- **Google Stitch Design System**
- **Firebase Authentication (Anônimo)**
- **Cloud Firestore (Tempo Real via `onSnapshot`)**
- **Open Exchange Rates API**
- **Google Fonts (Plus Jakarta Sans & Inter)**
- **Material Symbols**
