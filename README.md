# Orbita Play: site de teste do widget do SAC

Site de iGaming **fictício**, feito só para testar o widget de atendimento do [SAC](https://github.com/Yamargo/sacia). Não tem dinheiro real, jogos reais nem cadastro.

## Como abrir

**Link:** https://yamargo.github.io/teswebsite/

O GitHub Pages precisa estar ativado em **Settings → Pages → Deploy from a branch → `main` / `(root)`**.

### Modo teste (padrão)

O site usa o SAC de teste publicado em https://yamargo.github.io/sacia/. Como os dois ficam no mesmo domínio, o chat e o SAC trocam dados pelo próprio navegador. Para testar:

1. Abra https://yamargo.github.io/sacia/ e entre como `god@sac.local` / `Sac@2026`.
2. Crie um agente da linha 7987.
3. Em outra aba do **mesmo navegador**, entre com esse agente.
4. Em mais uma aba, abra https://yamargo.github.io/teswebsite/ e fale pelo balão. O chat chega para o agente.

### Com o servidor real (Railway)

Abra `https://yamargo.github.io/teswebsite/?sac=https://SEU-SAC.up.railway.app` ou preencha `SAC_SERVER` em `sac-config.js`. Assim pessoas em computadores diferentes se falam.

## O que testar

- **Balão:** fica no canto inferior direito. No celular, o chat abre em tela cheia.
- **Botões "Talk to support" e "Open live chat":** chamam `SAC.open()`.
- **Log in (demo):** entra como o jogador fictício `PLR-10293`. O nome e o ID já aparecem preenchidos no chat (`SAC.identify`), e o agente vê o ID no SAC.
- **Painel verde no topo:**
  - mostra o servidor em uso;
  - troca a linha (`7987`, `8557`);
  - chama `SAC.open()`, `SAC.identify()` e `SAC.setLanguage()`.

  Para testar outra linha, use `?linha=CODIGO` no endereço.

## Como o widget está instalado

O site carrega o widget do mesmo jeito que um site real carregaria:

```html
<script src="https://SEU-SAC/widget.js" data-linha="7987" data-idioma="auto" data-posicao="direita" async></script>
```

Aqui o `<script>` é criado pelo JavaScript da página, só para o endereço do servidor poder vir de `sac-config.js` ou do link.
