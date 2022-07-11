## Compilers

- Hexdump `xxd ./some.class | more` 


## Intepretadores e compiladores

Para criar um compilador, geralmente será necessário criar um analisador léxico e um analizador sintático que cria uma AST, após isso, o passo seguinte será utilizar um compilador llvm para otimizar o código via Transform Passes e gerar o binário.

### Análise léxica

- Faz a tokenização de dígitos, não-digitos, maiúsculo e minúsculo, caracteres
- Lex, flex -> tokenização léxica
- [ECMAScript Lexical Grammar](https://tc39.es/ecma262/#sec-ecmascript-language-lexical-grammar)

---

### Análise sintática

> In computer science, Backus–Naur form or Backus normal form (BNF) is a metasyntax notation for context-free grammars, often used to describe the syntax of languages used in computing, such as computer programming languages, document formats, instruction sets and communication protocols.

Análise sintática vai tokenizar as expression e criar uma Parse Tree de expressões : termos. Esse parser sintático é feito pela **Abstract Syntax Tree** (AST).

Notação infixa: é uma notação comum em aritmética e na lógica, onde os operadores são colocados entre os operandos em que eles atuam. Para os computadores é mais simples analisar a notação prefixa ou a posfixa do que analisar a infixa, mas muitas linguagens de programação a usam por causa de sua familiaridade.

<img src="./assets/notação-prefixa.png" width="50%">


- Bison, yacc -> análise sintática
- [ANSI C Yacc grammar](https://www.lysator.liu.se/c/ANSI-C-grammar-y.html)
- [ECMAScript Grammar Notation](https://tc39.es/ecma262/#sec-grammar-notation)


---

### Compile time


---

### Run time


---

### JIT

- Faz cache de binários mais acessados para aumentar a velocidade de carregamento. Após 'compilado' em código intermediário ainda é possível fazer alterações.
- Tem maior flexibilidade
- Executar código que altera o que está em execução
- Meta-progamação
- Vantagem do interpretador é injetar bytecodes sem reiniciar o programa.
- Alteração em tempo de execução


---

### AOT

- Compilador Static Linker linka os binários para acesso rápido. Após compilado não se pode mudar

---



### Referências

- [Backus–Naur form](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form)
- [LLVM](https://llvm.org/docs/Passes.html)
- [Static linking vs dynamic linking](https://stackoverflow.com/questions/1993390/static-linking-vs-dynamic-linking)
- [ANSI C Yacc grammar](https://www.lysator.liu.se/c/ANSI-C-grammar-y.html)