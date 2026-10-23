# Cronomaps — mapa histórico com busca inteligente

O conteúdo principal da interface, estilos, JavaScript e dados locais está reunido em `app/src/main/assets/index.html`.

## Recursos
- Mapa histórico interativo com marcadores, linha do tempo e acontecimentos simultâneos.
- Busca online em Wikipédia, Wikidata, Internet Archive e geocodificação OpenStreetMap/Nominatim.
- **Autocompletar:** ao digitar pelo menos três caracteres, o aplicativo sugere lugares, pessoas e entidades; toque numa sugestão para pesquisar e, quando for um lugar, aproximar o mapa.
- Navegação por teclado nas sugestões (setas, Enter e Esc), útil em dispositivos com teclado físico.
- Consultas de sugestões com atraso de 550 ms para reduzir pedidos repetidos enquanto se digita.

## Pastas dentro de `app/src/main`
- `assets/` — interface, CSS e JavaScript em `index.html`.
- `java/` — `MainActivity.kt`.

As demais pastas contêm configurações Android/Gradle e o workflow GitHub Actions necessários para gerar o APK. As buscas, imagens e os blocos do mapa dependem da internet e da disponibilidade das APIs públicas; não exigem uma chave de API privada.

## Gerar APK
Envie os arquivos do ZIP para o repositório GitHub mantendo a pasta oculta `.github`. Na aba **Actions**, execute o workflow Android. Se a compilação terminar com sucesso, baixe o artefato `cronomaps-apk`.
