### BDD

O Behavioral-Driven Development (BDD) é uma abordagem de teste derivada da metodologia Test-Driven Development (TDD). No BDD, os testes são baseados principalmente no comportamento do sistema. Essa abordagem define várias maneiras de desenvolver um recurso com base em seu comportamento. Na maioria dos casos, a abordagem Given-When-Then é usada para escrever casos de teste. Vamos a um exemplo para melhor compreensão:

- Dado que o usuário inseriu credenciais de login válidas.
- Quando um usuário clica no botão de login.
- Em seguida, exiba a mensagem de validação bem-sucedida

<img src="https://3fxtqy18kygf3on3bu39kh93-wpengine.netdna-ssl.com/wp-content/uploads/2019/10/Screenshot-2019-09-27-at-1.51.16-PM.png" width="50%">


### TDD

Desenvolvimento Orientado a Testes (Test-Driven Development) é uma metodologia de teste ou uma prática de programação implementada da perspectiva de um desenvolvedor. É necessário escrever casos de teste para cada pequena funcionalidade de um aplicativo. A principal intenção desta técnica é modificar ou escrever um novo código somente quando o teste falhar. Portanto, resulta em menor duplicação de scripts de teste. Em uma abordagem TDD, os scripts de teste automatizados são escritos antes das partes funcionais do código. A metodologia TDD envolve os seguintes passos:

- Com base nos requisitos especificados nos documentos, um desenvolvedor escreve um caso de teste automatizado
- Esses testes são executados e, em alguns casos, eles falham, pois são desenvolvidos antes do desenvolvimento de um recurso real
- A equipe de desenvolvimento então refatora o código para que o teste passe com sucesso

<img src="https://dkrn4sk0rn31v.cloudfront.net/2019/11/04105020/img-tdd.png" width="50%">

### ATDD

Na técnica de Desenvolvimento Orientado a Testes de Aceitação (ATDD), um único teste de aceitação é escrito a partir da perspectiva do usuário. Ele se concentra principalmente em satisfazer o comportamento funcional do sistema. Essa técnica tenta responder à pergunta – O código está funcionando conforme o esperado?

Nota: O Desenvolvimento Orientado a Testes de Aceitação é muito semelhante ao Desenvolvimento Orientado a Comportamento. No entanto, uma diferença fundamental entre eles é: o BDD se concentra mais no comportamento do recurso, enquanto o ATDD se concentra na captura dos requisitos precisos.

- Analisar e discutir os cenários do mundo real.
- Decidir os critérios de aceitação para esses cenários de teste.
- Automatizando os casos de teste de aceitação.
- Focando no desenvolvimento desses casos de requisitos

---

### Tests

> test && commit || revert - \Kent Beck