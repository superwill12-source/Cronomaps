# Cronomaps — mapa histórico com busca inteligente

O conteúdo principal da interface, estilos, JavaScript e dados locais está reunido em `app/src/main/assets/index.html`.

## Recursos
- Mapa histórico interativo com marcadores, linha do tempo e acontecimentos simultâneos.
- Busca online em Wikipédia, Wikidata, Internet Archive e geocodificação OpenStreetMap/Nominatim.
- **Autocompletar:** ao digitar pelo menos três caracteres, o aplicativo sugere lugares, pessoas e entidades; toque numa sugestão para pesquisar e, quando for um lugar, aproximar o mapa.
- Navegação por teclado nas sugestões (setas, Enter e Esc), útil em dispositivos com teclado físico.
- Consultas de sugestões com atraso de 550 ms para reduzir pedidos repetidos enquanto se digita.
- **Acontecimentos atuais pelo mundo:** painel inicial em tempo real aproxima ocorrências globais reportadas nas últimas 24 horas via GDELT, eventos ambientais ativos da NASA EONET e terremotos recentes do USGS. O painel pode ser fechado e reaberto pelo botão “O que acontece agora”; atualiza manualmente e tenta atualizar a cada 15 minutos enquanto estiver aberto. As localizações da cobertura GDELT representam lugares mencionados nos relatos, não necessariamente a posição exata do acontecimento.
- **Consolidação histórica:** combina feeds de acontecimentos do dia da Wikipédia em português e inglês, On This Day API, eventos com data e coordenadas do Wikidata, terremotos do USGS e eventos ambientais da NASA EONET quando disponíveis.
- **Diagnóstico por fonte:** mostra quantos registros cada serviço retornou ou se a consulta falhou, com botão para tentar novamente.
- **Mapa sem coordenadas inventadas:** acontecimentos sem localização confiável continuam na lista; coordenadas extraídas do artigo da Wikipédia são identificadas como aproximadas.
- A cobertura histórica depende dos registros existentes em cada base. O USGS cobre terremotos registrados a partir de 1900; o feed “neste dia” mostra aniversários históricos, e não afirma que todos ocorreram no ano selecionado.

## Pastas dentro de `app/src/main`
- `assets/` — interface, CSS e JavaScript em `index.html`.
- `java/` — `MainActivity.kt`.

As demais pastas contêm configurações Android/Gradle e o workflow GitHub Actions necessários para gerar o APK. As buscas, imagens, acontecimentos atuais e blocos do mapa dependem da internet e da disponibilidade das APIs públicas; as fontes GDELT, NASA EONET, USGS, Wikipédia e Wikidata não exigem uma chave de API privada nesta integração. A consulta ao vivo não foi validada em execução no Android neste ambiente.

## Gerar APK
Envie os arquivos do ZIP para o repositório GitHub mantendo a pasta oculta `.github`. Na aba **Actions**, execute o workflow Android. Se a compilação terminar com sucesso, baixe o artefato `cronomaps-apk`.


### Acontecimentos do Brasil e notícias por data
A busca de acontecimentos atuais inclui consultas específicas a fontes brasileiras, além do feed global, NASA EONET e USGS. Ao alterar o ano/data na linha do tempo, o app consulta fontes de acontecimentos históricos e, para datas a partir de 2017, tenta recuperar reportagens arquivadas do GDELT para o dia selecionado. A cobertura depende das fontes e nem toda notícia tem coordenadas; nesses casos ela não pode virar marcador no mapa.
