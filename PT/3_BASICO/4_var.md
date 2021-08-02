[Home](../HomePT.md) • [3.4 Variáveis](#)

# Variáveis


Na programação uma variável é um objeto capaz de reter e representar um valor ou expressão. Ela é armazenada na sua memória RAM. 

No C# nós estruturamos a variável escolhendo a sua `tipagem` seguindo com seu `nome`.

```csharp
int life = 5;
float speed = 4f;
string say = "my name";
bool isAlive = true;
```
## Int

A variável tipo `int` recebe números **inteiros** 
(ex:-1,0,1,2,3,...,7,8).

A `int` pode ser utilizada para compor uma barra de vida, mostrando quanto de dano um inimigo sofreu após um ataque.

## Float

A variável tipo `float` recebe números quebrados/trabalha com casas decimais (ex: -0.1, ..., 0.3, 0.54, 0.89, ..., 4.567).

A `float` pode ser utilizada para compor a velocidade de um personagem. Recomenda-se a `float` ao invés da `int` nesses casos por uma questão de balanceamento.

por exemplo: ao atribuir o valor `3` a velocidade do personagem você achou muito lento, e ao atribuir `4` você achou muito rápido. Pra balancear você pode aplicar a `float` e utilizar um numero quebrado como `3.7f`

**Todo valor utilizando a variavel float deve ser acompanhado de um F (`5.1f`)**

## String

A variável tipo `string` recebe caracteres.

Ela pode ser utilizada para compor um diálogo entre dois personagens do seu jogo.

## Bool

A variável tipo `bool` ou `Booleana` recebe valores de `verdadeiro` e `falso`.

Ela pode ser utilizada em situações de comparação, por exemplo para informar a engine se seu personagem esta vivo ou não `isDead = true;`

## Escopo de Variáveis

Variáveis possuem escopo de acesso, ou seja, dependendo de onde declarar essa variável ela não será acessada fora do escopo dela. Portanto, é possível ter duas declarações de variáveis com o mesmo nome, porém em escopos diferentes.

Toda variável criada dentro de um bloco de código `{ }` terá esse bloco de código como seu escopo, não podendo ser acessada fora dele.

```csharp

public class TesteEscopo
{
    public void AcessandoVariaveis()
    {
        int numero1 = 1;

        if(numero1 == 1)
        {
            int numero2 = 2;
        }

        numero1 = numero2;
    }
}
```

Ao executar o código irá aparecer o seguinte erro:

```
 error CS0103: The name 'numero2' does not exist in the current context
```

Isso quer dizer que você está tentando acessar uma variável que não existe no escopo atual do `numero1`. `numero2` foi criada dentro do escopo do if, então só será possível acessar ela de dentro do if.

## Modificadores de acesso
O C# utiliza o conceito de modificadores de acessos. Os mais comuns são `private` e `public` cuja a funcionalidade é bastante sugestiva. Esses modificadores de acesso são utilizados para declarar propriedades de classe ou objeto.

Uma variável `private` é limitada a sua classe de origem e só pode ser acessada somente dentro da própria classe. 

Uma variável `public` pode ser acessada de fora de sua classe, ou seja, você pode acessa-la chamando a variável em alguma outra classe.

Exemplo:

```csharp
public class PlayerController
{
    private Vector2 movement;
    public int life = 10;
}

public class TestePlayerController
{
    public void AcessandoModificadorPublico()
    {
        PlayerController playerController = new PlayerController();
        int playerLife = playerController.life; //vai ser possível recuperar quantos pontos de vida o player tem por ser uma variável public

        Vector2 playerMovement = playerController.movement; // NÃO VAI FUNCIONAR por ser private, ou seja, você só pode utilizar ela somente dentro do PlayerController
    }
}
```

No Unity, os modificadores de acesso podem, também, tornar a variável acessível pelo inspetor para terem seus valores modificados na UI do Unity. Então, se utilizar uma variável `public`, ela irá aparecer no inspetor. Porém, é possível deixar as variáveis privadas (`private`) disponíveis no inspetor utilizando o atributo `[SerializeField]` na declaração da variável.

```csharp
public class PlayerController : MonoBehaviour
{
    [SerializeField]
    private Vector2 movement;
    public int life = 10;
}
```

Agora é possível ver tanto o movement quanto a life no inspetor.

Também é possível remover o acesso da propriedade pelo inspetor utilizando a propriedade ```[NonSerialized]```

```csharp
public class PlayerController : MonoBehaviour
{
    [NonSerialized]
    public Vector2 movement;
    public int life = 10;
}
```

Nem sempre queremos que uma variável seja acessada por outra classe ou objeto, mas queremos ter ela disponível para fácil acesso no inspetor. Para isso usamos o **[SerializeField]** para solucionar esse problema.

Avançar [3.5 Debug](./5.debug.md)

