# Auditoria GitHub Pages — 01/09/2026

A URL publicada `https://pulseads.github.io/supremeclube/` exibe apenas o título `supremeclube` sobre uma página branca. A screenshot do repositório mostra que a raiz contém `README.md` e um único arquivo `supreme-clube-git-ready.zip`; o código da aplicação não foi extraído para a raiz do repositório.

## Diagnóstico

O GitHub Pages está servindo o README porque não encontra um `index.html` na raiz publicada. O ZIP não é executado pelo GitHub Pages. Além disso, a versão local usa caminhos persistentes `/manus-storage/...`, que não são portáveis para o GitHub Pages sem copiar os assets para o próprio repositório ou usar URLs públicas equivalentes.

## Correção necessária

Preparar uma distribuição GitHub Pages com `index.html`, `assets/` e bundles gerados no nível publicado; configurar a base para `/supremeclube/`; substituir referências de assets Manus por assets locais versionados ou URLs públicas; manter o limite de 25 MB; e documentar a configuração correta do GitHub Pages.
