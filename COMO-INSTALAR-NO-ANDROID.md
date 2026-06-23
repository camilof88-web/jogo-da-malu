# 📱 Como transformar a "Aventuras da Malu" em app de Android

O jogo agora é um **PWA** (um site que se comporta como app: abre em tela cheia, tem ícone
e funciona **sem internet**). Pra virar um `.apk` instalável no celular, são 2 partes:

1. **Subir o jogo num link** (GitHub Pages — de graça)
2. **Gerar o `.apk`** a partir desse link (PWABuilder — de graça)

---

## Arquivos do app (os que precisam ir pro GitHub)

- `index.html`  ← o jogo
- `manifest.webmanifest`  ← nome, ícone e configurações do app
- `sw.js`  ← faz funcionar sem internet
- `icons/icon-192.png` e `icons/icon-512.png`  ← os ícones

> O arquivo `jogo-da-malu-v4.html` é só um **backup** da versão antiga — não precisa subir.
> A pasta `.claude` também não precisa.

---

## PARTE 1 — Subir no GitHub Pages

1. Entre no [github.com](https://github.com) e clique em **New** (novo repositório).
2. Dê um nome, por exemplo **`jogo-da-malu`**.
3. Deixe marcado como **Public** (público). *É necessário pro GitHub Pages gratuito e pro PWABuilder conseguir ler o link.*
4. Clique **Create repository**.
5. Na página do repositório, clique em **Add file → Upload files**.
6. **Arraste** pra lá: `index.html`, `manifest.webmanifest`, `sw.js` e a **pasta `icons`** inteira.
7. Clique em **Commit changes** (botão verde).
8. Vá em **Settings** (engrenagem do repositório) → no menu da esquerda, **Pages**.
9. Em **Source**, escolha **Branch: `main`** e pasta **`/ (root)`** → clique **Save**.
10. Espere 1–2 minutos e recarregue. Vai aparecer um link assim:
    **`https://SEU-USUARIO.github.io/jogo-da-malu/`**
11. Abra esse link no celular pra testar. Já dá pra jogar! (e, se quiser, já dá pra
    "Adicionar à tela inicial" pelo menu do navegador.)

✅ Guarde esse link — você vai usar na Parte 2.

---

## PARTE 2 — Gerar o `.apk` com o PWABuilder

1. Acesse [pwabuilder.com](https://www.pwabuilder.com).
2. **Cole o link** do GitHub Pages (o do passo 10) e clique **Start**.
3. Ele analisa o app. Deve aparecer uma nota boa (manifest ✓ e service worker ✓).
4. Clique em **Package For Stores** → escolha **Android**.
5. Em opções de assinatura (**Signing key**), deixe **"Create new"** (criar nova).
   - ⚠️ **Importante:** o PWABuilder vai gerar uma **chave** (`.keystore`) e mostrar umas
     **senhas**. **Guarde tudo num lugar seguro.** Você só vai precisar disso se um dia quiser
     atualizar o app na Play Store — pra uso em casa, não é crítico, mas guarde mesmo assim.
6. Clique em **Download**. Vem um arquivo `.zip`.
7. Dentro do zip tem o **`.apk`** (e um arquivo de instruções).

### Instalar no celular dela
1. Mande o `.apk` pro celular (WhatsApp pra você mesmo, cabo USB, ou Google Drive).
2. Toque no arquivo `.apk` no celular.
3. O Android vai pedir pra permitir **"instalar apps de fontes desconhecidas"** — autorize.
4. Toque em **Instalar**. Pronto: o ícone da Malu aparece na tela inicial! 🌟

---

## Tela cheia (tirar a barrinha do navegador) — opcional, mas recomendado

O PWABuilder também te dá um arquivo chamado **`assetlinks.json`** e diz pra colocá-lo numa
pasta **`.well-known`** do seu repositório. Faça isso (Add file → Create new file → nome
`.well-known/assetlinks.json` → cole o conteúdo que o PWABuilder mostrou → Commit).
Isso faz o app abrir **em tela cheia de verdade**, sem a barrinha de endereço do navegador.

---

## E pra ATUALIZAR o jogo depois?

A melhor parte: o `.apk` gerado é uma "casquinha" que abre o seu site do GitHub.
Então, quando a gente melhorar o jogo, é só **subir os arquivos novos no GitHub** —
o app instalado pega a versão nova sozinho (na próxima vez com internet).
**Não precisa gerar o `.apk` de novo** a cada mudança. 🎉
