# Painel do Editor Mínimo

App de registro diário das edições de vídeo da Mínimo Marketing.
Cada editor entra com a própria conta (e-mail e senha) e vê só os próprios registros.

Endereço: https://painel-do-editor.web.app

## Como subir do zero

1. Crie um repositório novo no GitHub (pode ser privado).
2. Na página do repositório, clique em "uploading an existing file" e arraste
   TODO o conteúdo desta pasta, inclusive a pasta `.github` e os arquivos
   `.firebaserc`, `.gitignore` e `firebase.json`. Confirme em "Commit changes".
3. No computador, com o Node instalado, baixe o repositório e rode dentro da pasta dele:

       npx firebase-tools login
       npx firebase-tools init hosting:github

   Respostas: repositório = seu-usuario/nome-do-repo;
   "build script" = No; "deploy when a PR is merged" = Yes; branch = main.
   Se perguntar se pode sobrescrever os arquivos da pasta `.github`, responda No.
   Isso cria no GitHub o segredo `FIREBASE_SERVICE_ACCOUNT_PAINEL_DO_EDITOR`.
4. Faça qualquer alteração e um novo commit na branch main (ou, no GitHub,
   vá em Actions > Publicar no Firebase Hosting > Re-run). Em 1 a 2 minutos o app está no ar.

## No console do Firebase (projeto painel-do-editor)

- Authentication > Método de login: E-mail/senha ativado.
- Firestore Database > Regras: colar o conteúdo de `firestore.rules` e publicar.

## Atualizações

Toda vez que um arquivo novo entra na branch main, o GitHub publica sozinho.
Ao mudar o app, aumente a versão do cache em `sw.js` (ex.: painel-editor-v3 para v4)
para que quem instalou receba a versão nova.
