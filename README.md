# Crono Maps

Aplicativo Android em português para explorar assuntos históricos, com pesquisa local/offline, busca online na Wikipédia em português, linha do tempo e globo interativo de fallback.

## O que está implementado

- Projeto Android nativo em Kotlin com WebView e interface HTML/CSS/JavaScript.
- Pesquisa local tolerante a maiúsculas/minúsculas e acentos, com base inicial em `app/src/main/assets/web/data/eventos.json`.
- Pesquisa online sem chave paga usando a API da MediaWiki (quando há internet).
- Resultados com resumo, período/local quando disponíveis, fontes externas e detalhes.
- Linha do tempo de 3000 a.C. a 2026 d.C. e lista de registros locais ativos no ano selecionado.
- Marcadores e rotação/zoom por toque em um globo esquemático interativo.
- Histórico de pesquisas recentes no armazenamento local do navegador.
- GitHub Actions compila e publica o APK debug como artefato.

## Limitações transparentes

- O globo atual é uma representação esquemática 2D interativa, **não** é um globo 3D real, Google Earth, mapa de satélite ou mapa histórico. O módulo isolado `globe.js` pode ser substituído por Three.js ou outra solução.
- A busca online consulta a Wikipédia em português; não é uma busca universal em todas as fontes nem uma verificação acadêmica. Os dados locais são demonstrativos e limitados. Use os links de fonte para confirmar detalhes.
- Imagens, notícias atuais, OpenHistoricalMap, Wikidata e Commons ainda não estão integrados.
- Fontes externas e fontes web precisam de conexão. A interface e a base local funcionam sem internet. A tipografia do Google Fonts é opcional; sem rede usa fontes do sistema.
- Datas históricas podem ser aproximadas; o app indica incerteza quando cadastrada na base.

## Compilar pelo GitHub Actions (sem editar arquivos no celular)

1. Baixe e descompacte `crono-maps.zip`.
2. No GitHub, crie um repositório vazio chamado `crono-maps`.
3. No celular, abra o repositório pelo navegador e use **Add file → Upload files**. Envie os arquivos e pastas que estão dentro da pasta `crono-maps` descompactada (incluindo `.github`). Se o navegador não permitir enviar diretórios ocultos, use um cliente Git que preserve `.github` ou envie o ZIP para um ambiente que permita `git push`.
4. Faça commit na branch `main` (ou `master`). O workflow está em `.github/workflows/android.yml` e roda em `push` para ambas.
5. Também é possível abrir a aba **Actions**, selecionar **Android APK** e tocar em **Run workflow**.
6. Abra a execução mais recente concluída, vá a **Artifacts** e baixe `crono-maps-apk`.
7. Descompacte o artefato e instale `app-debug.apk`. Talvez seja necessário permitir a instalação de apps dessa origem nas configurações Android.

## Compilação local

Requer JDK 17 e Android SDK 35. Com Gradle instalado:
```bash
gradle --no-daemon assembleDebug
```
Saída esperada: `app/build/outputs/apk/debug/app-debug.apk`.

## Licenças e atribuição

A API e o conteúdo da Wikipédia seguem os termos da Wikimedia; consulte [termos de uso](https://foundation.wikimedia.org/wiki/Policy:Terms_of_Use) e [atribuição](https://en.wikipedia.org/wiki/Wikipedia:Reusing_Wikipedia_content). Artigos externos podem ter licenças próprias. Os textos da base local são resumos introdutórios escritos para este projeto e cada registro aponta uma fonte de referência.
