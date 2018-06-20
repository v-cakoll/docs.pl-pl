---
title: Kompilowanie drzew wyrażeń
description: Więcej informacji o technikach tworzenia drzewa wyrażeń.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7751af17aafa8e2d1a14125da43352108b1c1f95
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207192"
---
# <a name="building-expression-trees"></a>Kompilowanie drzew wyrażeń

[Poprzedniej — Interpretowanie wyrażenia](expression-trees-interpreting.md)

Wszystkie drzewa wyrażeń, które w tym samouczku wykonanej do tej pory zostały utworzone przez kompilator języka C#. Wszystkie musiał wykonać zostały Tworzenie wyrażenia lambda, która została przypisana do zmiennych wpisanych w formie `Expression<Func<T>>` lub podobnego typu. To nie jest jedynym sposobem, aby utworzyć drzewo wyrażenia. W różnych scenariuszach może się okazać, że jest potrzebne do tworzenia wyrażenia w pamięci w czasie wykonywania. 

Tworzenie drzewa wyrażeń jest złożona przez fakt, że te drzew wyrażeń są niezmienne. Trwa niezmienne oznacza, że utworzenie drzewa liści do katalogu głównego. Interfejsy API, zostanie użyta do tworzenia drzewa wyrażeń odzwierciedlają fakt: metody, zostanie użyta do tworzenia węzła przyjmują wszystkie elementy podrzędne jako argumenty. Przejdźmy kilka przykładów pokazanie technik.

## <a name="creating-nodes"></a>Tworzenie węzłów

Zacznijmy stosunkowo po prostu ponownie. Użyjemy wyrażenie dodawania I używane w tych sekcjach:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Można utworzyć tego drzewa wyrażenia, należy tworzyć węzłów liści.
Węzły liści są stałe, dzięki czemu można używać `Expression.Constant` metodę w celu utworzenia węzłów:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Następnie będzie Zbuduj wyrażenie dodatku:

```csharp
var addition = Expression.Add(one, two);
```

Po skonfigurowaniu wyrażenie dodanie można utworzyć wyrażenia lambda:

```csharp
var lambda = Expression.Lambda(addition);
```

Jest to wyrażenie lambda bardzo proste, ponieważ zawiera bez argumentów.
Później w tej sekcji, zobaczysz sposób mapowania argumenty parametrów i tworzenie bardziej złożonych.

Wyrażeń, które są tak proste, jak ta mogą łączyć wszystkie wywołania do jednej instrukcji:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Tworzenie drzewa

To podstawy tworzenia drzewa wyrażeń w pamięci. Bardziej złożone drzew zazwyczaj oznacza więcej typów węzłów i większą liczbę węzłów w drzewie. Teraz uruchomić za pomocą jednego więcej przykład i Pokaż dwóch więcej typy węzłów, które zwykle utworzysz podczas tworzenia drzewa wyrażeń: argument węzłów i węzły wywołania metody.

Utworzymy drzewo wyrażenia, aby utworzyć tego wyrażenia:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Użytkownik rozpoczyna się przez utworzenie parametr wyrażenia dla `x` i `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Tworzenie wyrażeń mnożenia i dodawania jest zgodny ze wzorcem został już wcześniej:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Następnie należy utworzyć wyrażenie wywołania metody dla wywołania `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

A następnie na koniec, Umieść wywołanie metody do wyrażenia lambda i upewnij się, że do definiowania argumentów do wyrażenia lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

W tym przykładzie bardziej skomplikowany zobacz temat kilka więcej techniki, które często będą potrzebne do tworzenia drzewa wyrażeń.

Najpierw należy utworzyć obiekty, które reprezentują parametry lub zmienne lokalne przed ich użyciem. Po utworzeniu tych obiektów, można używać ich w Twojej drzewo wyrażeń, jeśli potrzebujesz.

Po drugie, należy użyć podzestawu interfejsów API odbicia do utworzenia `MethodInfo` obiekt, w którym można utworzyć drzewa wyrażeń na dostęp do tej metody. Należy ograniczyć się do podzestawu interfejsów API odbicia, które są dostępne na platformie .NET Core. Ponownie te techniki może trwać do innego drzewa wyrażeń.

## <a name="building-code-in-depth"></a>Kompilowanie kodu szczegółowo

Nie są ograniczone w przypadku można utworzyć za pomocą tych interfejsów API. Jednak bardziej skomplikowane drzewo wyrażeń, który chcesz utworzyć, trudniej kod jest do zarządzania i do odczytu. 

Utworzymy drzewo wyrażenia, który jest odpowiednikiem ten kod:

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

Powyżej zauważyć, że nie zbudować drzewo wyrażeń, ale po prostu delegata. Przy użyciu `Expression` klasa, nie można utworzyć instrukcji lambda. Oto kod, który jest wymagany do kompilacji te same funkcje. Jest złożona faktem, że nie ma interfejsu API do tworzenia `while` pętli, zamiast tego należy utworzyć pętli, które zawiera test warunkowy i elementem docelowym etykiety w celu wyjścia z pętli. 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

Kod służący do tworzenia drzewa wyrażenia funkcji silni jest dość nieco dłużej, bardziej skomplikowane i jest on riddled z etykiety i instrukcje break i innymi elementami, które chcielibyśmy uniknąć w naszym codziennie kodowania zadań. 

W tej sekcji również po aktualizacji kodu odwiedzający odwiedź każdy węzeł w drzewie tego wyrażenia i zapisywanie informacji o węzłach, które są tworzone w tym przykładzie. Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) w repozytorium GitHub dotnet/docs. Eksperymentu dla siebie przez tworzenia i uruchamiania przykładów. Instrukcje pobrania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Badanie interfejsy API

Drzewo wyrażeń interfejsy API są trudniejsze do nawigacji w .NET Core, ale się. Ich celem jest raczej złożonych przedsiębiorstwa: pisanie kodu, który generuje kod w czasie wykonywania. Są one zawsze skomplikowane, aby zapewnić równowagę między obsługi dostępna w języku C# struktury sterujące i utrzymywanie jak uzasadnione powierzchni interfejsów API. Saldo to oznacza, że wiele struktury sterujące są reprezentowane nie przez ich konstrukcji języka C#, ale przez konstrukcje reprezentujących podstawowej logiki, które kompilator generuje na podstawie tych konstrukcji wyższego poziomu. 

Ponadto w tej chwili brak C# wyrażeń, które nie może zostać utworzony bezpośrednio przy użyciu `Expression` metody klasy. Ogólnie rzecz biorąc będzie to być najnowszej operatory i wyrażenia dodane w języku C# 5 i 6 C#. (Na przykład `async` wyrażenia nie może zostać utworzony, a nowe `?.` operatora nie można bezpośrednio utworzyć.)

[Next — Tłumaczenia wyrażenia](expression-trees-translating.md)
