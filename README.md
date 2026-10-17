# Sistema de Missões: como colocar no ar e no iPhone

Esta pasta é o app completo (HTML + ícone + modo offline). Ele funciona como um PWA: abre em tela cheia no iPhone, com ícone próprio.

## Caminho 1: grátis e rápido (recomendado para começar)

1. Hospede esta pasta em um serviço gratuito. Exemplos: Netlify Drop (arraste a pasta no site), Cloudflare Pages ou GitHub Pages.
2. Você recebe um link https. Mande esse link para quem quiser usar.
3. No iPhone, abra o link no Safari, toque em Compartilhar e escolha "Adicionar à Tela de Início".

Cada pessoa tem o próprio progresso, salvo no próprio aparelho.

## Caminho 2: App Store (mais trabalhoso)

Precisa de:
- Um Mac com Xcode.
- Conta no Apple Developer Program (US$ 99 por ano).

Passos com o Capacitor (no Terminal do Mac, com Node.js instalado):

```
mkdir missoes-ios && cd missoes-ios
npm init -y
npm i @capacitor/core @capacitor/cli @capacitor/ios
npx cap init "Sistema de Missões" com.seunome.missoes --web-dir=www
mkdir www   # copie index.html, manifest.webmanifest, sw.js e os ícones para dentro de www
npx cap add ios
npx cap sync
npx cap open ios
```

No Xcode: escolha seu time (conta Apple), configure o ícone e envie para a App Store Connect em Product > Archive.

Atenção: a Apple costuma recusar apps que são só um site dentro de um aplicativo (diretriz 4.2, funcionalidade mínima). Para aumentar a chance de aprovação, adicione recursos nativos de verdade, como lembretes de treino por notificação local e integração com o app Saúde. Inclua também política de privacidade e avisos de que as estimativas de dieta e peso não substituem um profissional de saúde.

## Importante: recursos de IA

A "Dieta inteligente" e a busca automática de alimentos só funcionam dentro do Claude. Fora dele, elas ficam escondidas automaticamente e o resto do app funciona normalmente. Para ter IA no app próprio, é preciso um servidor seu que chame a API da Anthropic (nunca coloque a chave de API dentro do app).
