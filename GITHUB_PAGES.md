# Supreme Clube no GitHub Pages

Este projeto é uma aplicação React/Vite. O arquivo `index.html` não deve ser aberto diretamente no computador, porque o navegador não compila os arquivos TypeScript/React. A publicação deve ser feita a partir do código-fonte, com o build executado pelo GitHub Actions.

## Publicação recomendada

Extraia o ZIP e envie **o conteúdo da pasta do projeto** para a raiz do repositório GitHub. Não envie o ZIP como um único arquivo e não publique a pasta `dist` manualmente.

No terminal, dentro da pasta extraída, execute:

```bash
git init
git branch -M main
git add .
git commit -m "Publicar landing page Supreme Clube"
git remote add origin https://github.com/pulseads/supremeclube.git
git push -u origin main
```

Se o repositório já tiver um remote configurado, use somente:

```bash
git add .
git commit -m "Corrigir publicação no GitHub Pages"
git push
```

No GitHub, abra **Settings → Pages** e selecione **GitHub Actions** como fonte de publicação. O workflow `.github/workflows/deploy-pages.yml` instala as dependências, executa o build com a base `/supremeclube/` e publica `dist/public` automaticamente.

Depois que o workflow terminar, a URL esperada é:

```text
https://pulseads.github.io/supremeclube/
```

## Alternativa pelo upload da interface

Na página do repositório, use **Add file → Upload files**, arraste os arquivos e pastas já extraídos e confirme o commit na branch `main`. Garanta que `.github/workflows/deploy-pages.yml` também foi enviado; sem esse arquivo, o GitHub não terá a rotina de build.

## Desenvolvimento local

Com Node.js 22 e pnpm instalados:

```bash
pnpm install
pnpm dev
```

Abra a URL indicada pelo Vite, normalmente `http://localhost:3000/`. Para validar a produção:

```bash
pnpm check
GITHUB_ACTIONS=true pnpm build
```

O resultado fica em `dist/public`. O pacote público gerado nesta versão tem aproximadamente 6,6 MB, e o repositório-fonte compactado sem dependências instaladas permanece abaixo de 25 MB.

## Observações de funcionamento

Os assets da landing page estão locais em `client/public/assets`, e a imagem de fundo do hero também é processada pelo Vite para respeitar o subdiretório do GitHub Pages. As ações de agendamento continuam separadas: estética automotiva pelo WhatsApp comercial e barbearia pelo número de agendamento informado.

O vídeo possui `controls`, poster e áudio. Como os navegadores normalmente bloqueiam autoplay com som, ele começa somente quando o visitante inicia a reprodução. O chatbot permanece discreto, abre sob solicitação e oferece apenas menus de orientação e encaminhamento para WhatsApp, sem inventar preços ou disponibilidade.

O mapa usa o componente integrado ao projeto Manus no desenvolvimento local. No GitHub Pages, a página principal continua funcional mesmo que a API de mapas não seja carregada; o endereço e o link externo para a localização permanecem disponíveis como alternativa.
