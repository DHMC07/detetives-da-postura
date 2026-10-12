# Detetives da Postura (Ergonomia, 5.º ano TIC)

| Ficheiro | Para quê |
|---|---|
| `index.html` | Exercício dos alunos (sem login) |
| `professor.html` | Área do professor: entregas, validação, listas, configuração |
| `estilos.css` | Aspeto das duas páginas |
| `firebase-config.js` | Ligação ao seu projeto Firebase (**tem de preencher**) |
| `firestore.rules` | Regras de segurança (**cole na consola da Firebase**) |

## 1. Firebase (uma vez, ~10 min)
1. Em <https://console.firebase.google.com> crie um projeto (o plano gratuito Spark chega).
2. **Build > Firestore Database > Create database**, modo de produção, região `eur3` ou a mais próxima.
3. **Build > Authentication > Get started > Sign-in method** e ative:
   - **Anonymous** (os alunos entram sem darem por isso);
   - **Email/Password** (só para si).
4. **Authentication > Users > Add user**: crie a sua conta de professor (um email e uma palavra-passe forte). Copie o **User UID**.
5. Abra `firestore.rules`, troque `COLE_AQUI_O_SEU_UID` pelo seu UID, e cole o ficheiro todo em **Firestore > Rules > Publish**.
6. **Definições do projeto (⚙️) > As suas apps > Web (</>)**: registe a app e copie o objeto `firebaseConfig` para `firebase-config.js`.

## 2. GitHub Pages
1. Crie um repositório (ex.: `detetives-da-postura`) e carregue os 5 ficheiros na raiz.
2. **Settings > Pages > Deploy from a branch > main / (root) > Save**.
3. Ao fim de 1–2 min fica disponível em:
   - Alunos: `https://SEU-UTILIZADOR.github.io/detetives-da-postura/`
   - Professor: `https://SEU-UTILIZADOR.github.io/detetives-da-postura/professor.html`
4. Na Firebase, em **Authentication > Settings > Authorized domains**, adicione `SEU-UTILIZADOR.github.io`.

## 3. Primeira utilização
1. Entre em `professor.html` > **Configuração**: confirme turmas (A–F), missões e mínimo de regras > Guardar.
2. Em **Entregas > Lista da turma**, cole a lista de alunos de cada turma.
3. Dê aos alunos só o link principal (ex.: no Classroom).

## Como funciona
- O aluno escreve nome e turma; o progresso é enviado automaticamente em cada missão. Sem internet, fica guardado no computador e é enviado na próxima abertura.
- Pode **Validar**, **Devolver ao aluno** (com comentário, o aluno vê-o no mapa e pode corrigir) ou **Eliminar**.
- Depois de validar, o trabalho fica bloqueado e os dados do aluno são **apagados do computador dele na próxima vez que o exercício for aberto nesse computador**.
- **Exportar CSV** abre no Excel ou no Google Sheets.

## Notas
- O `apiKey` no `firebase-config.js` é público por natureza; a proteção está nas regras da Firestore (os alunos não conseguem ler entregas de outros nem alterar trabalhos validados).
- Para testar no seu computador use um servidor local (ex.: extensão *Live Server* do VS Code); abrir o ficheiro com duplo clique não funciona por causa dos módulos JavaScript.
