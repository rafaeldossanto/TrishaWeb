# trilha_web

Front web (desktop) do **Trisha** — a mesma base visual do app mobile
(`trilha_app`), adaptada para o browser: side nav estilo Instagram em janelas
largas, conteudo central com largura maxima por tela e o mapa colaborativo
full-bleed como home.

## Rodar em dev

Suba o back com o profile `dev` (Cadastro `:8080`, BFF `:8090`, loc `:8082`,
midia `:8083`) e:

```
flutter run -d chrome
```

O `.env` ja aponta para `localhost` (o CORS do BFF e da midia libera
`http://localhost:*` em dev).

## Diferencas em relacao ao trilha_app

- **Web-only**: so a plataforma `web/` e gerada.
- `MainShell` responsivo: `>=900px` side nav (rotulos a partir de `1150px`);
  abaixo disso, a bottom bar original.
- Telas empurradas no root navigator usam o wrapper `WebPage` (coluna central
  com largura maxima); telas de mapa/rastreio seguem em tela cheia.
- Upload de midia por bytes (`XFile.readAsBytes`) — na web nao existe caminho
  de arquivo.
- `scrollBehavior` habilita arrastar listas/carrosseis com mouse e trackpad.

## Build de producao

```
flutter build web --release
```

Artefato em `build/web/` (estatico, serve em qualquer HTTP server).
