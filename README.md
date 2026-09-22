# Imagens — mastersdameia.com.br

Este repositório contém todas as imagens do site, organizadas por página:

- `images/home/` — imagens da página principal (curso)
- `images/sobremim/` — imagens da página Sobre Mim
- `images/ebook/` — capas dos ebooks
- `images/depoimentos/` — prints usados na página de Depoimentos
- `images/logo.png` — logo compartilhado por todas as páginas

## Como publicar no GitHub

1. Crie um repositório **público** vazio no GitHub (ex: `masters-da-meia-assets`). Público é necessário para o CDN jsDelivr funcionar de graça.
2. Rode os comandos abaixo, substituindo `SEU_USUARIO` e `NOME_DO_REPO`:

```bash
cd github-assets-repo
git remote add origin https://github.com/SEU_USUARIO/NOME_DO_REPO.git
git push -u origin main
```

3. Me avise o link do repositório (`github.com/SEU_USUARIO/NOME_DO_REPO`).

## O que acontece depois

Assim que o repositório estiver no ar, eu troco todas as referências `/images/...` e `/logo.png` do site pelas URLs do CDN jsDelivr, que serve arquivos de repositórios GitHub públicos com cache de verdade (ao contrário do `raw.githubusercontent.com`, que não é feito para isso em produção):

```
https://cdn.jsdelivr.net/gh/SEU_USUARIO/NOME_DO_REPO@v1/images/home/02-fernando-reis.jpg
```

Uso uma tag de versão fixa (`@v1`) em vez de `@main`, para que trocar uma imagem no futuro não quebre o cache de quem já visitou o site. Quando eu fizer essa troca, crio a tag `v1` no repositório (`git tag v1 && git push origin v1`).

Até lá, o site já funciona normalmente servindo essas imagens localmente (pasta `images/` dentro do próprio site) — o ganho de performance de ter tirado tudo do base64 já está valendo, o jsDelivr é uma camada extra de otimização.
