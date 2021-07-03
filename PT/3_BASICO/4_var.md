[Home](../HomePT.md) • [3.4 Variáveis](#)

# Variáveis


Na programação uma variável é um objeto capaz de reter e representar um valor ou expressão. 

No C# nós estruturamos a variável escolhendo a sua `tipagem` seguindo com seu `nome`.

```
int life = 5;
float speed = 4f;
string say = "my name";
bool isAlive = true;
```
## Int

A variável tipo `int` ela recebe números **inteiros** 
(ex:-1,0,1,2,3,...,7,8).

A `int` pode ser utilizada para compor uma barra de vida, mostrando quanto de dano um inimigo sofreu após um ataque.

## Float

A variável tipo `float` ela recebe números quebrados/trabalha com casas decimais (ex: -0.1, ..., 0.3, 0.54, 0.89, ..., 4.567).

A `float` pode ser utilizada para compor a velocidade de um personagem. Recomenda-se a `float` ao invés da `int` nesses casos por uma questão de balanceamento.

por exemplo: ao atribuir o valor `3` a velocidade do personagem você achou muito lento, e ao atribuir `4` você achou muito rápido. Pra balancear você pode aplicar a `float` e utilizar um numero quebrado como `3.7f`

**Todo valor utilizando a variavel float deve ser acompanhado de um F (`5.1f`)**

## String

A variável tipo `string` ela recebe caracteres.

Ela pode ser utilizada para compor um diálogo entre dois personagens do seu jogo.

## Bool

A variável tipo `bool` ou `Booleana` ela recebe valores de `verdadeiro` e `falso`.

Ela pode ser utilizada em situações de comparação, por exemplo para informar a engine se seu personagem esta vivo ou não `isDead = true;`

## Privacidade de Variáveis

O C# utiliza o conceito `private` e `public` cuja a funcionalidade é bastante sugestiva.

Uma variável `private` é limitada a sua classe de origem e só pode ser acessada por membros ou métodos locais. 

Uma variável `public` pode ser acessada de qualquer classe e por qualquer componente.

A Unity complementa esse conceito com os atributos 
`[SerializeField]` e `[NonSerializeField]`.

### Pós e Contras 

**[SerializeField]**

Avançar [3.5 Debug](./5.debug.md)

