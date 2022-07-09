# ✨ JavaScript ES6 

[descrição sobre o que é o javascript e como ele funciona, como os navegadores o utilizam e etc]

## Principais tópicos

- [Scope](#escope)

## Scope <a id="scope"></a>

Escopo é a acessibilidade de objetos, variáveis e funções em diferentes partes do código de uma aplicação.
- Escopo Global
  - Uma variável global é uma variável declarada fora de uma função ou bloco e, por conta disso, é acessível em qualquer parte da aplicação. 
- Escopo Local
  - Já uma variável de escopo local é uma variável declarada dentro de uma função, ficando acessível apenas no escopo dessa função e restrita ao resto da aplicação.
- Escopo de Bloco
  - Intruduzido no ES6, uma variável com escopo de bloco é uma variável declarada dentro de um bloco (estruturas de repetição, decisão, etc) e acessível apenas nele. As variáveis com esse escopo devem ser declaradas com `let` ou `const`.

> **Essa questão de escopo ajuda a responder a questão: qual a diferença entre let, const e var.**
> - `const`: têm escopo de bloco, não permite redeclaração e nem modificação do valor
> - `let`: tem escopo de bloco, não permite redeclaração, mas o valor da variável pode ser modificado
> - `var`: não tem escopo de bloco, permite redeclaraçaõ de modificação do valor → *por esses motivos o seu uso não é indicado*


