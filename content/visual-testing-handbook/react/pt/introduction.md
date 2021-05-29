---
title: 'Introdução a testes visuais'
tocTitle: 'Introdução'
description: 'A forma programática de testar interfaces'
---

Interfaces são subjetivas. A resposta para a pergunta "isso está certo?" depende do seu navegador, dispositivo e gosto pessoal. No fim, você ainda precisa verificar a interface renderizada para checar a aparência.

O problema é que leva muito tempo para verificar toda a interface manualmente a cada commit. Existem algumas maneiras de tentar automatizar um certo teste visual, através de testes unitários/snapshots. O problema é que estes métodos normalmente falham, pois máquinas não conseguem validar se uma interface está correta a partir de tags HTML ou classes CSS.

Como times previnem bugs visuais? Quais técnicas players como a Microsoft, BBC e Shopify usam para entregar interfaces para milhões de pessoas? Meu co-autor Tom e eu pesquisamos a resposta em times incríveis para entender o que de fato funciona.

Este guia introduz o conceito de testes visuais, uma forma programática que combina a assertividade de um olho humano com a eficiência de uma máquina. Ao invés de remover o fator humano do teste, os testes visuais utilizam de ferramentas para focar o esforço em alterações específicas na interface que realmente precisam de atenção.

![O caminho para testes visuais](/visual-testing-handbook/visual-testing-handbook-vtdd-path-optimized.png)

## Testes unitários não possuem olhos

Para falarmos de testes visuais, faz sentido partirmos de testes unitários. Interfaces modernas são [orientadas à componentes](https://componentdriven.org/) – compostas por partes modulares. O construtor de um componente permite que você renderize uma interface como uma função com props e states. Isso significa que você pode testar componentes unitariamente, como qualquer outra função.

Um teste unitário isola um módulo e verifica o seu comportamento. Ele realiza a inserção de props, states, etc., e compara o resultado recebido com o esperado. Testes unitários são recomendados pois testar módulos isoladamente faz com que fique mais fácil cobrir mais casos e identificar a raíz de problemas.

<video autoPlay muted playsInline loop>
  <source
    src="/visual-testing-handbook/component-unit-testing.mp4"
    type="video/mp4"/>
</video>

O principal problema é que muito da complexidade de uma interface está em seu próprio visual, ou seja, a forma específica a qual o HTML e o CSS são renderizados na tela do usuário.

Testes unitários são perfeitos para testar coisas concretas, como por exemplo: `2 + 2 === 4`. Mas elas não são tão boas para testar interfaces, já que é complicado diferenciar quais detalhes do HTML e do CSS impactam a aparência, já que, não é sempre, por exemplo, que uma alteração no HTML afeta de fato o visual da interface.

## E quanto a testes por snapshots?

[Testes por snapshots](https://reactjs.org/docs/testing-recipes.html#snapshot-testing) oferecem uma alternativa para verificar a aparência de uma interface. Eles renderizam o componente e então tomam a DOM gerada como uma "linha de base". Desta forma, as alterações geradas na DOM são comparadas com esta linha de base. Se houverem diferenças, o desenvolvedor precisa explicitamente atualizar a linha de base.

![Código de componente](/visual-testing-handbook/code-visual-testing-optimized.png)

Ná prática, os snapshots da DOM não são tão eficientes, pois é um tanto quanto complicado determinar como uma interface foi renderizada através da verificação de um HTML minificado.

Testes por snapshots acabam sofrendo do mesmo problema de outros testes de interface automatizados. Qualquer mudança interna no funcionamento de um componente acaba pedindo por um teste novo, ainda que este não traga consigo impacto visual.

## Testes visuais foram feitos para interfaces

Os testes visuais foram feitos para capturar alterações feitas na interface. Usando um explorador de componentes como o Storybook para isolar os componentes você mocka as suas variações, e por fim, salva os cases de teste suportados como "stories".

Em ambiente de desenvolvimento, você faz uma rápida verificação manual do componente renderizando-o no navegador, para checar como ficou, podendo validar cada variação do componente através do explorador e suas stories.

<video autoPlay muted playsInline loop>
  <source
    src="/visual-testing-handbook/storybook-toggling-stories.mp4"
    type="video/mp4"/>
</video>

Em ambiente de QA, você utiliza algum tipo de automação para detectar mudanças e assegurar a consistência da sua interface. Ferramentas como o [Chromatic](https://www.chromatic.com/) capturam uma imagem (snapshot) de cada case de teste, contendo o markup, estilos e outros assets, num ambiente consistente tal como um navegador.

Em cada commit, um novo snapshot é automaticamente comparado com à ultima linha de base aceita. Quando uma diferença visual é detectada, o desenvolvedor recebe uma notificação para aprovar a mudança, ou então, arrumar um bug que surgiu na interface.

<video autoPlay muted playsInline loop>
  <source
    src="/visual-testing-handbook/component-visual-testing.mp4"
    type="video/mp4"/>
</video>

#### Isso parece ser muito trabalhoso...

Apesar de soar trabalhoso, esse fluxo acaba sendo mais fácil do que ficar verificando falsos positivos de testes automatizados de interface, ou então atualizando cases de teste para ficarem de acordo com pequenas alterações, e ainda, trabalhando a mais para fazer com que os testes continuem passando.

## Aprendendo a usar a ferramenta

Agora que nós temos uma noção maior acerca de testes visuais, vamos verificar a principal ferramenta que você precisa para utiliza-la: um explorador de componentes. No próximo capítulo veremos como exploradores de componentes ajudam desenvolvedores a construirem e testarem seus componentes.
