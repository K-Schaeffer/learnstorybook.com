---
title: 'Explorador de componentes'
tocTitle: 'Explorador de componentes'
description: 'Uma ferramenta para desenvolvimento e testes visuais de interfaces'
---

Interfaces de usuário modernas suportam diversas variantes de state, idioma, dispositivo, navegador e dados do usuário. No passado o desenvolvimento de interfaces costumava ser bastante ineficiente. Era necessário navegar para uma página específica em um dispositivo específico com as configurações específicas. Após isso, ainda era necessário clicar pela página para que pudesse deixa-la no state correto para conseguir começar a programar.

**Um explorador de componentes isola a interface da regra de negócio e do contexto da aplicação.** Com isso você consegue construir uma interface de forma isolada, focando em cada componente e suas determinadas variações. Isso permite que você identifique como inputs (props, states) afetam a interface que foi renderizada e forma a base da sua suíte de testes visuais.

[Storybook](https://storybook.js.org/) é um explorador de componentes padrão na indústria, e é ele que nós iremos utilizar para demonstrar os testes visuais. Ele é utilizado pelo Twitter, Slack, Airbnb, Shopify, Stripe e outras milhares de empresas, então você poderá aplicar o conhecimento adquirido nesse guia independentemente de onde você for trabalhar.

<video autoPlay muted playsInline loop>
  <source
    src="/visual-testing-handbook/storybook-component-explorer-visual-testing.mp4"
    type="video/mp4"/>
</video>

## Por que construir interfaces de forma isolada?

### Menos bugs

Quanto mais componentes e states você possui, mais difícil é confirmar se de fato tudo foi renderizado corretamente nos dispositivos e navegadores dos usuários.

Exploradores de componentes previnem inconsistências através de uma amostra das variações suportadas do componente. Isso faz com que os desenvolvedores consigam focar em cada state de maneira independente. Com isso você consegue testa-los isoladamente, além de que em casos de fluxos mais extremos você ainda pode usar mocks.

![Cases de teste de componentes](/visual-testing-handbook/component-test-cases.png)

### Mais produtividade

Aplicações nunca estão totalmente finalizadas, pois as melhorias e iterações são constantes. Sendo assim, a arquitetura das interfaces precisa ser adaptável para suportar novas funcionalidades. O modelo de componentes encoraja intercambiabilidade através da segmentação de interfaces e a regra de negócio.

Exploradores de componentes fazem essa separação ficar ainda mais evidente, provendo uma sandbox para desenvolver as interfaces isoladamente, longe da aplicação. Na prática, isso significa que equipes podem trabalhar em diferentes partes da interface simultaneamente sem distrações ou "poluição" de states de outras partes da aplicação.

### Mais colaboratividade

Interfaces são inevitavelmente visuais, portanto, pull requests com apenas códigos são uma representação incompleta do trabalho realizada. Para obter uma colaboratividade maior as partes interessadas precisam olhar para a interface.

Exploradores de componentes olham para as interfaces e todas as suas variações. Isso faz com que fique mais fácil obter um feedback de outros desenvolvedores, designers, testers, etc.

<video autoPlay muted playsInline loop>
  <source
    src="/visual-testing-handbook/storybook-workflow-publish.mp4"
    type="video/mp4"/>
</video>

## Onde isso se encaixa na minha stack?

Um explorador de componentes é um pequeno pacote standalone que permanece em harmonia com a sua aplicação, ou seja, não a afeta. Ele permite que você visualize variações dos componentes de forma isolada, e contém as seguintes funcionalidades:

- 🧱 Componentes isolados em um Sandbox
- 🔭 Visualizador de variação para as especificações e propriedades do componente
- 🧩 Possibilidade de salvar variações como "stories" para revisita-las durante os testes
- 📑 Documentação e guia de utilização dos componentes

![Relação entre componentes e exploradores de componentes](/visual-testing-handbook/storybook-relationship.png)

## Aprendendo o fluxo de trabalho

Isolar a sua interface com um explorador de componentes lhe dá a possibilidade de realizar testes visuais. O próximo capítulo mostra como reformular o TDD (Test-Driven Development) para o desenvolvimento de interfaces.
