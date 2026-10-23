# Cronomaps — estrutura mínima

O conteúdo da interface, estilos, JavaScript e dados locais está reunido em `app/src/main/assets/index.html`.

## Pastas dentro de `app/src/main`
- `assets/` — um único arquivo `index.html`.
- `java/` — um único arquivo `MainActivity.kt`.

As demais pastas na raiz são arquivos de configuração do Android/Gradle e do GitHub Actions, necessários para compilar o APK automaticamente. A busca online usa a API pública da Wikipédia. O globo agora usa Globe.gl para renderizar a Terra em 3D, com textura terrestre, contornos dos países, rotação por toque/arraste, zoom e marcadores históricos. A textura, a biblioteca e os contornos dependem de conexão com a internet.

## Gerar APK
Envie todos os arquivos do ZIP para um repositório GitHub mantendo a pasta oculta `.github`. Na aba Actions, execute o workflow Android. O APK de depuração será disponibilizado como artefato `cronomaps-apk` se a compilação terminar com sucesso.
