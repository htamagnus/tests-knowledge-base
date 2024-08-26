## Topics:

### 1. Introdução aos Testes Automatizados
- Definição e importância dos testes automatizados.
- Problemas com testes manuais: tempo, custo, e a necessidade de re-testar após mudanças.

### 2. A Pirâmide de Testes (Mike Cohn)
- **Explicação da pirâmide**: diferentes camadas de testes, organizadas do mais simples ao mais complexo.
- **Imagem da pirâmide**: representar visualmente os tipos de testes.

### 3. Testes de Unidade 🧩
- **Definição**: Verificação de pequenas partes do código (funções ou classes).
- **Exemplo prático**: Testar peças isoladas do "quebra-cabeça".
- **Vantagens**: Testes rápidos, fáceis de implementar e de rodar.
- **Proporção recomendada**: 70% de testes de unidade.

### 4. Testes de Integração 🔗
- **Definição**: Testes que verificam a interação entre diferentes partes do sistema.
- **Exemplo prático**: Como peças de quebra-cabeça que se encaixam.
- **Objetivo**: Testar a integração de módulos com sistemas reais, como banco de dados.
- **Testes com APIs externas**: Mocking, testes em ambiente real e uso de contratos de API (ferramentas como Pact).
- **Proporção recomendada**: 20% de testes de integração.

### 5. Testes de Sistema / Interface com o Usuário (End-to-End) 🖥️
- **Definição**: Testes de ponta a ponta, simulando o uso real do sistema.
- **Ferramentas**: Selenium, Cypress, Puppeteer.
- **Exemplos avançados**: Integração com CI/CD, simulação de falhas de rede, testes em múltiplos dispositivos.
- **Proporção recomendada**: 10% de testes de sistema.

### 6. Princípios FIRST para Testes de Unidade
- **Fast**: Testes devem ser rápidos.
- **Independent**: Testes devem ser independentes uns dos outros.
- **Repeatable**: Devem ter os mesmos resultados em cada execução.
- **Self-checking**: O resultado deve ser claro e direto.
- **Timely**: Escrever testes no momento certo (preferencialmente antes).

### 7. Estratégias de Teste: TDD e Bug Fixing
- **Test-Driven Development (TDD)**: Escrever testes antes do código.
- **Testes após encontrar bugs**: Escrever testes que revelem e confirmem a correção de bugs.

### 8. Benefícios dos Testes Automatizados 🚀
- **Identificar bugs cedo**: Encontrar problemas rapidamente durante o desenvolvimento.
- **Prevenir regressões**: Garantir que novas alterações não quebrem funcionalidades já existentes.
- **Documentar e especificar comportamento**: Testes servem como documentação funcional do sistema.

### 9. Desafios Comuns e Soluções
- **Manutenção de testes**: Ajustar testes conforme o código evolui.
- **Testes acoplados**: Reduzir o acoplamento entre testes e implementação, focando no comportamento.
- **Falsos positivos e negativos**: Como garantir que os testes sejam precisos e confiáveis.

### 10. Testes de Performance ⚡
- **Ferramentas**: Chrome DevTools, Lighthouse, Benchmark.js.
- **Estratégias**: Testes de latência, carga e profiling de código.
- **Boas práticas**: Minimizar manipulação de DOM, otimizar loops e funções, evitar uso excessivo de memória.

### 11. Testes de Mutação 🧬
- **Definição**: Introduzir erros intencionais para verificar se os testes captam as alterações.
- **Ferramentas**: Stryker para JavaScript.

### 12. Testes Baseados em Propriedades 🔁
- **Definição**: Verificar se determinadas propriedades são sempre mantidas em diversas entradas.
- **Ferramenta**: fast-check.

### 15. Cobertura de Código 📊
- **Ferramentas**: jest --coverage, nyc (Istanbul).
- **Interpretação dos resultados**: A importância de uma boa cobertura de testes.

### 16. Conclusão e Recomendações Finais
- **Proporção de testes**: 70% unidade, 20% integração, 10% sistema.
- **Manutenção e qualidade**: Como garantir que os testes acompanhem o desenvolvimento.

---

# Testes Automatizados 🤖

Fazer testes manualmente, ou seja, uma pessoa sentar e testar tudo passo a passo, leva muito tempo, custa caro e é um trabalho que ninguém quer fazer. Além disso, sempre que algo no programa muda, tem que testar tudo de novo… Para entender melhor os testes automatizados, existe uma coisa chamada pirâmide de testes, que foi uma ideia do Mike Cohn. Imagine uma pirâmide dividida em partes, onde cada parte mostra um tipo diferente de teste, organizados do mais simples e rápido lá embaixo até os mais complexos e demorados no topo. Essa pirâmide ajuda a entender que nem todos os testes são iguais: alguns são básicos e outros são bem detalhados, mas todos são importantes para garantir que o programa funcione direitinho.

![Piramide de Testes](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F6sxij6lciz3zyy26q67e.png)

1. Na base da pirâmide, temos os **testes de unidade**. Eles são como checar as peças de um quebra-cabeça uma por uma para ter certeza de que cada uma está certa. Cada teste desses olha para uma pequena parte do programa (geralmente uma única função ou classe) para ver se ela está fazendo o que deveria. Esses testes são muitos, rápidos de rodar e fáceis de fazer.

![Testes de Unidade](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F7x9otqr32n0dqh3f9htv.png)

2. No meio da pirâmide, encontramos os **testes de integração** ou testes de serviços. Imagine tentar ver se algumas peças do quebra-cabeça se encaixam como deveriam. Estes testes olham como diferentes partes do programa trabalham juntas. Por exemplo, eles podem testar se o programa salva as informações certinho no banco de dados. Esses testes são um pouco mais complexos que os testes de unidade e demoram mais para serem feitos e rodados.

    Nos testes de integração você não usa mocks ou stubs, pois o objetivo é interagir com o sistema real, como um banco de dados. Assim, você terá uma instância real do banco de dados em seu teste, que deve estar configurado para um ambiente de teste, idealmente usando uma base de dados que possa ser limpa ou recriada antes de cada teste para garantir a consistência.

    Testes de integração geralmente são mais lentos do que testes de unidade devido à sua complexidade e à necessidade de interagir com sistemas externos.

    Ao executar testes de integração, você está verificando não apenas a lógica do negócio, mas também a integração dessa lógica com outras partes do sistema, assegurando que o sistema como um todo funcione conforme o esperado.

### Testes de Integração com APIs Externas

- **Mocking de APIs Externas**: Quando o código depende de APIs externas, é importante garantir que os testes possam isolar a aplicação do ambiente externo. Para isso, bibliotecas como `nock` podem ser usadas para simular respostas de APIs em testes de integração.
- **Testes com Ambiente Real**: Em alguns casos, pode ser necessário testar diretamente com a API externa em um ambiente de staging. Aqui, é crucial lidar com os tempos de resposta e cenários de erro que podem surgir da dependência de um serviço externo.
- **Contratos de API**: Usar testes de contrato para garantir que as APIs externas mantenham as respostas esperadas. Ferramentas como Pact ajudam a validar a consistência das interações entre serviços.

![Testes de Integração](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fbav68okk4fs08ugsul00.png)

3. No topo da pirâmide, temos os **testes de sistema** ou **testes de interface com o usuário**. Isso é como pegar o quebra-cabeça montado e ver se a imagem final está certa. Estes testes verificam o programa inteiro, de ponta a ponta, do jeito que um usuário de verdade usaria. São os testes mais complexos, mais demorados para rodar e custam mais caro. Eles também são "frágeis", o que quer dizer que pequenas mudanças no programa podem fazer com que esses testes precisem ser ajustados.

    Testes de sistema são uma simulação completa de como um usuário real interage com o aplicativo, de ponta a ponta. São os testes mais abrangentes e, por isso, geralmente os mais caros e os que levam mais tempo para serem executados.

    Para automatizar testes de sistemas Web em JavaScript, você pode usar ferramentas como Selenium ou alternativas modernas como Cypress ou Puppeteer. Essas ferramentas permitem que você escreva scripts de teste que interagem com o navegador, assim como um usuário real faria.

- **Integração de Testes E2E no CI/CD**: Configurar uma pipeline de integração contínua que roda testes end-to-end automaticamente ao fazer o deploy da aplicação. Isso garante que todas as funcionalidades essenciais da aplicação sejam verificadas antes de cada lançamento.
- **Testes de Falhas de Rede**: Simular falhas de rede e verificar como a aplicação reage quando uma API está fora do ar, ou quando há delays significativos. Ferramentas como Cypress e Puppeteer permitem simular diferentes cenários de rede.
- **Simulação de Dispositivos e Resoluções**: Em testes de E2E de front-end, é fundamental garantir que a aplicação funcione corretamente em múltiplos dispositivos e tamanhos de tela. Ferramentas como BrowserStack e Sauce Labs permitem rodar testes em diferentes navegadores e dispositivos reais.

![Testes de Sistema](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Farzkd7k5bdux6yr1jdbe.png)

Uma recomendação genérica é que esses três testes sejam implementados na seguinte proporção: 70% como testes de unidades; 20% como testes de serviços e 10% como testes de sistema.

---

### Princípios FIRST

Quando se fala em escrever testes de unidade de boa qualidade, há alguns princípios básicos, agrupados na sigla **FIRST**, que podem ajudar bastante.

- **Fast ⚡**: Os testes de unidade devem sempre ser rápidos. A ideia é que você consiga rodá-los o tempo todo, sem ficar esperando. Se você precisa de um café enquanto seus testes rodam, provavelmente eles não são rápidos o suficiente.

- **Independent 🧍‍♂️**: Cada teste de unidade deve ser capaz de se virar sozinho. Não importa a ordem que você decide rodá-los; eles não devem depender uns dos outros.

- **Repeatable 🔁**: Se você rodar o mesmo teste várias vezes, o resultado deveria ser sempre o mesmo: ou o teste sempre passa, ou sempre falha. Testes que às vezes passam e às vezes falham sem motivo aparente são chamados de "flaky" ou erráticos.

- **Self-checking ✅**: Uma vez finalizada a execução dos testes, o resultado deve ser auto-explicativo (passou/falhou). Desta forma, o resultado pode ser ligeiramente verificado e interpretado.

- **Timely 🕰️**: É uma boa ideia escrever os testes de unidade o quanto antes no seu processo de desenvolvimento. Muita gente até prefere escrever os testes antes do código que eles vão testar, isso ajuda a garantir que o seu código vai fazer exatamente o que você espera desde o começo.

---

### Quando testar e quando não testar

Escrever testes de unidade é como se preparar para uma prova: você estuda um tópico e faz um teste para ver se realmente aprendeu. Existem duas formas principais de fazer isso:

- **Depois de Programar**: Você cria uma parte do seu programa, como uma função que soma dois números. Depois de fazer isso funcionar, você escreve um teste que verifica se, quando você soma 2 e 2, o resultado é realmente 4. Você continua assim, criando mais partes do seu programa e escrevendo testes para cada uma.

- **Antes de Programar (TDD)**: Esse é o método Test-Driven Development (Desenvolvimento Orientado por Testes). Aqui você faz ao contrário: escreve o teste para a função de soma antes mesmo de fazer a função. Claro, o teste vai falhar, porque a função ainda não existe. Depois, você cria a função de forma que faça o teste passar. Isso ajuda a manter o foco em fazer apenas o necessário para que a função cumpra sua tarefa.

Além de escrever testes antes ou depois de desenvolver, tem mais duas maneiras inteligentes de usar os testes de unidade:

- **Quando Aparecer um Bug**: Imagine que alguém te conta que encontrou um erro no seu programa. Uma ótima maneira de começar a resolver isso é escrevendo um teste que mostra esse erro acontecendo. Assim, você tem um teste que falha porque o programa não está fazendo o que deveria. Depois, você conserta o erro e, se o teste passar, você não só corrigiu o problema como também ganhou um novo teste para garantir que esse erro não volte a acontecer no futuro.

- **Durante a Depuração**: Se você está tentando entender por que uma parte do seu programa não está funcionando, resista à tentação de só jogar um monte de `console.log` para ver o que está acontecendo. Em vez disso, é melhor escrever um teste que verifica o comportamento que você está tentando consertar. Isso te ajuda a ser mais sistemático na depuração e ainda te deixa com um teste útil no final.

**Quando não testar:**

- **Não deixe para o final**: Esperar até que todo o programa esteja pronto para começar a testar geralmente não é uma boa ideia. Isso porque você pode acabar fazendo os testes com pressa e de forma superficial, ou pior, pode acabar não fazendo os testes de jeito nenhum. Além disso, testar tudo de uma vez pode ser muito mais complicado e menos eficiente do que testar pedacinho por pedacinho à medida que você constrói o programa.

- **Não divida a responsabilidade**: É tentador pensar que alguém pode fazer o programa e outra pessoa pode testá-lo. Mas na verdade, é super importante que quem escreveu um pedaço do código também escreva os testes para esse código. Isso ajuda a garantir que os testes estão cobrindo o que realmente importa e que o desenvolvedor entende profundamente como seu código deve funcionar.

---

### Benefícios 🚀

- **Encontrar Bugs Cedo**: A ideia é pegar os problemas enquanto você ainda está desenvolvendo, antes de tudo ficar mais complicado (e caro) para consertar. Se você tem bons testes, é menos provável que erros chatos surpreendam você ou seus usuários lá na frente.

- **Evitar Regressões**: Uma "regressão" é quando você muda alguma coisa no código para melhorar ou adicionar algo novo, mas acaba estragando outra coisa sem querer. Com testes de unidade, se você fizer uma mudança que cause uma regressão, provavelmente vai descobrir rápido porque um dos seus testes vai falhar.

- **Documentar e Especificar**: Além de te ajudar a não quebrar coisas, os testes também contam uma história sobre como seu código deve se comportar. Se alguém quiser entender melhor uma parte do seu programa, pode começar olhando os testes para ver o que esperar dele. É quase como se os testes fossem um manual de instruções que mostra como usar e o que esperar do seu código.

---

### Desafios comuns

#### Manutenção de Testes

- **Problema**: À medida que o código evolui, os testes também precisam ser ajustados para refletir as mudanças. Manter os testes atualizados e em sincronia com o código pode ser demorado e frustrante.
- **Solução**: Escreva testes que sejam fáceis de adaptar e mantenha uma boa separação de responsabilidades no código, para que mudanças não afetem vários testes ao mesmo tempo. Refatorar os testes regularmente é tão importante quanto refatorar o código.

#### Testes Muito Acoplados ao Código

- **Problema**: Testes fortemente acoplados à implementação podem exigir muitas mudanças sempre que o código for refatorado, mesmo que o comportamento esperado não tenha sido alterado.
- **Solução**: Escreva testes baseados em comportamentos (BDD - Behavior Driven Development) ao invés de testar detalhes de implementação. Focar no output esperado e não em como o código está funcionando internamente pode reduzir esse acoplamento.

#### Falsos Positivos e Negativos

- **Problema**: Falsos positivos (testes que passam mesmo quando há um erro no código) e falsos negativos (testes que falham indevidamente) podem reduzir a confiança nos testes automatizados.
- **Solução**: Certifique-se de que os testes cubram casos de uso reais e que as asserções sejam precisas. Evite sobrecarregar os testes com múltiplas verificações que não estão diretamente relacionadas ao objetivo do teste.

---

### Testes de Performance: Como testar o desempenho do código JavaScript

Os testes de performance têm o objetivo de garantir que o código JavaScript seja executado de forma eficiente, especialmente em sistemas ou aplicações de grande escala. Eles ajudam a identificar gargalos e otimizar trechos que podem impactar a experiência do usuário ou o uso de recursos, como memória e tempo de processamento. Aqui estão algumas formas de realizar testes de desempenho em JavaScript:

#### Ferramentas para Testes de Performance

- **Google Chrome DevTools**: Oferece uma aba de “Performance” que permite analisar o desempenho do código em tempo real, mostrando métricas como o uso da CPU, a execução de scripts e a renderização do DOM. Também fornece informações detalhadas sobre os tempos de execução de cada função.
- **Node.js Profiler**: Se o código estiver sendo executado no servidor (Node.js), o `--prof` flag pode ser usado para gerar um relatório de desempenho detalhado. https://betterstack.com/community/guides/scaling-nodejs/profiling-nodejs-applications/

#### Estratégias de Teste de Performance

- **Testes de Latência e Tempo de Resposta**: Verificar quanto tempo uma operação leva para ser executada. Isso pode incluir medir o tempo de execução de funções, o carregamento de componentes ou até mesmo a execução de chamadas a APIs.
- **Testes de Carga**: Simular múltiplos usuários acessando a aplicação ao mesmo tempo para verificar como o código responde sob pressão. Isso é fundamental para garantir que o sistema suporte um grande número de requisições simultâneas.
- **Profiling de Código**: Utilizar ferramentas de profiling para identificar funções ou partes do código que estão consumindo muitos recursos (CPU ou memória) e precisam de otimização.
- **A/B Testing**: Comparar o desempenho de duas ou mais implementações de um código ou funcionalidade para decidir qual é a mais eficiente.

#### Melhores Práticas

- **Minimizar a Manipulação de DOM**: Manipular o DOM de forma excessiva pode prejudicar o desempenho. Sempre que possível, faça mudanças de uma só vez ou use técnicas como “debounce” e “throttle” para limitar a frequência das atualizações.
- **Otimizar Loops e Funções Pesadas**: Funções que realizam operações pesadas ou loops longos podem ser gargalos. Avalie a complexidade das funções e tente reduzir o número de iterações ou a profundidade dos loops.
- **Evitar Memória Desnecessária**: Cuidado com o uso excessivo de memória em coleções de dados grandes, objetos ou variáveis desnecessárias, que podem gerar memory leaks.

---

### Testes de Mutação

- **Mutation Testing** é uma técnica avançada que envolve modificar (mutar) o código propositalmente para verificar se os testes conseguem detectar as mudanças. O objetivo é medir a eficácia dos testes.
    - **Exemplo**: Se uma função `sum(a, b)` for mutada para retornar `a - b` em vez de `a + b`, os testes devem falhar, indicando que o conjunto de testes é robusto o suficiente para detectar essa alteração.
    - **Ferramentas**: Stryker é uma ferramenta popular para testes de mutação em JavaScript.

[Mais sobre Testes de Mutação](https://dev.to/paulogoncalvesr/testes-de-mutacao-1c7p)

---

### Testes Baseados em Propriedades

- Ao invés de verificar saídas específicas, os testes baseados em propriedades focam em verificar que determinadas propriedades se mantêm verdadeiras em diversas entradas. Esse tipo de teste é útil para verificar a robustez de algoritmos ou funções matemáticas.
- Ferramentas como **fast-check** permitem realizar testes baseados em propriedades no JavaScript.
    - **Exemplo**: Verificar que a função `sort()` sempre retorna uma lista com os mesmos elementos e que está ordenada.

---

### Cobertura de Código

- Introduzir ferramentas como o `jest --coverage` e o `nyc` (Istanbul) para medir a cobertura dos testes.
- Explicar como interpretar os resultados e a relevância de uma boa cobertura de testes.

---
