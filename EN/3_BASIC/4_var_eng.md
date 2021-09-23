[Home](../HomeEN.md) • [3.4 Variables](#)

## Variables

In programming, a variable is an object that get and represent some value or expression. It is storaged at your memory RAM. In C# we organize the variable choosing your `type` following with the `name`.

```csharp
int life = 5;
float speed = 4f;
string say = "my name";
bool isAlive = true;
```

## Int

The `int` variable receive **integer** numbers (ex:-1,0,1,2,3,...,7,8).

A `int` can be used to make a life bar, showing how much damage the enemy takes after an attack.

## Float

The `float` variable work with decimal number. A decimal number can be defined as a number whose whole number part and the fractional part is separated by a decimal point (ex: -0.1, ..., 0.3, 0.54, 0.89, ..., 4.567).

The `float` variable can be used to make the player's velocity. We recommend to use `float` instead of `int` duo balance.

For example: to assign the value `3` to the player movement speed, you figure out that is too slow, but after tried assign the value `4` you figure out that is too fast. So you can apply a `float` with a number like `3.7f` to balance it.

**Every value that is assign with float variable should be followed by an F (`5.1f`)**

## String

The `string` variable receive characters. It can be used to make a dialogue between two characters of your game.

## Bool

The `bool` ou `Boolean` variable receive values of `true` and `false`. It can be used to in comparison situation

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