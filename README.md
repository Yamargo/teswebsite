# Orbita Play: site de teste do widget do SAC

Site de iGaming **fictício**, feito só para testar o widget de atendimento do [SAC](https://github.com/Yamargo/sacia). Não tem dinheiro real, jogos reais nem cadastro.

## Como abrir

1. Ative o GitHub Pages: **Settings → Pages → Deploy from a branch → `main` / `(root)`**.
2. Abra o site informando o endereço do seu SAC no Railway:

   ```
   https://yamargo.github.io/teswebsite/?sac=https://SEU-SAC.up.railway.app
   ```

   O endereço fica salvo no navegador. Nas próximas vezes, basta abrir `https://yamargo.github.io/teswebsite/`.

Para deixar o endereço fixo para todo mundo, edite `sac-config.js`:

```js
window.SAC_SERVER = 'https://SEU-SAC.up.railway.app';
window.SAC_LINE = '7987';
```

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
