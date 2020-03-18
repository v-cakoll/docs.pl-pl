---
title: Drzewa wyrażeń budowlanych
description: Dowiedz się więcej o technikach budowania drzew wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146050"
---
# <a name="building-expression-trees"></a>Drzewa wyrażeń budowlanych

[Poprzedni -- Interpretacja wyrażeń](expression-trees-interpreting.md)

Wszystkie drzewa wyrażeń, które widziałeś do tej pory zostały utworzone przez kompilator C#. Wszystko, co musisz zrobić, to utworzyć wyrażenie lambda, który `Expression<Func<T>>` został przypisany do zmiennej wpisane jako lub podobny typ. To nie jedyny sposób tworzenia drzewa wyrażeń. W wielu scenariuszach może się okazać, że należy utworzyć wyrażenie w pamięci w czasie wykonywania.

Budowanie drzewa wyrażenia jest skomplikowane przez fakt, że te drzewa wyrażeń są niezmienne. Bycie niezmiennym oznacza, że musisz zbudować drzewo od liści do korzenia. Interfejsy API, których użyjesz do tworzenia drzew wyrażeń, odzwierciedlają ten fakt: Metody, których użyjesz do utworzenia węzła, przyjmują wszystkie jego elementy podrzędne jako argumenty. Przejdźmy przez kilka przykładów, aby pokazać techniki.

## <a name="creating-nodes"></a>Tworzenie węzłów

Zacznijmy stosunkowo po prostu od nowa. Użyjemy wyrażenia dodawania, z którym pracowałem w tych sekcjach:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Aby skonstruować to drzewo wyrażeń, należy skonstruować węzły liścia.
Węzły liścia są stałymi, dzięki `Expression.Constant` czemu można użyć metody do utworzenia węzłów:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Następnie stworzysz wyrażenie dodawania:

```csharp
var addition = Expression.Add(one, two);
```

Po uzyskaniu wyrażenia dodawania można utworzyć wyrażenie lambda:

```csharp
var lambda = Expression.Lambda(addition);
```

Jest to bardzo proste wyrażenie lambda, ponieważ nie zawiera żadnych argumentów.
W dalszej części tej sekcji zobaczysz, jak mapować argumenty na parametry i tworzyć bardziej skomplikowane wyrażenia.

W przypadku wyrażeń, które są tak proste, jak ten, można połączyć wszystkie wywołania w jednej instrukcji:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Budowanie drzewa

To podstawy budowania drzewa wyrażeń w pamięci. Bardziej złożone drzewa zazwyczaj oznacza więcej typów węzłów i więcej węzłów w drzewie. Przejdźmy przez jeszcze jeden przykład i pokaż dwa więcej typów węzłów, które zazwyczaj będą tworzyć podczas tworzenia drzew wyrażeń: węzłów argumentów i węzłów wywołania metody.

Skompilujmy drzewo wyrażeń, aby utworzyć to wyrażenie:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

Rozpoczniesz od utworzenia wyrażeń parametrów dla `x` i: `y`

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Tworzenie wyrażeń mnożenia i dodawania jest zgodne z wzorcem, który już widziałeś:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Następnie należy utworzyć wyrażenie wywołania metody dla `Math.Sqrt`wywołania .

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

I na koniec, można umieścić wywołanie metody w wyrażeniu lambda i upewnij się, że zdefiniowanie argumentów do wyrażenia lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

W tym bardziej skomplikowanym przykładzie zobaczysz kilka technik, które często będą potrzebne do utworzenia drzew wyrażeń.

Najpierw należy utworzyć obiekty, które reprezentują parametry lub zmienne lokalne przed ich użyciem. Po utworzeniu tych obiektów można ich używać w drzewie wyrażeń w dowolnym miejscu.

Po drugie, należy użyć podzbioru interfejsów API odbicia, aby utworzyć `MethodInfo` obiekt, aby można było utworzyć drzewo wyrażeń w celu uzyskania dostępu do tej metody. Należy ograniczyć się do podzbioru interfejsów API odbicia, które są dostępne na platformie .NET Core. Ponownie, techniki te obejmie inne drzewa wyrażeń.

## <a name="building-code-in-depth"></a>Szczegółowy kod budynku

Nie są ograniczone w co można tworzyć przy użyciu tych interfejsów API. Jednak bardziej skomplikowane drzewo wyrażeń, które chcesz utworzyć, tym trudniej jest zarządzać i czytać.

Skompilujmy drzewo wyrażeń, które jest odpowiednikiem tego kodu:

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

Zauważ powyżej, że nie skompilowałem drzewa wyrażeń, ale po prostu pełnomocnika. Za `Expression` pomocą klasy, nie można utworzyć lambdas instrukcji. Oto kod, który jest wymagany do tworzenia tych samych funkcji. Jest to skomplikowane przez fakt, że nie ma interfejsu `while` API do tworzenia pętli, zamiast tego należy utworzyć pętlę, która zawiera test warunkowy i cel etykiety, aby wyrwać się z pętli.

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

Kod do tworzenia drzewa wyrażeń dla funkcji faktorii jest nieco dłuższy, bardziej skomplikowany i jest pełen etykiet i instrukcji break i innych elementów, których chcielibyśmy uniknąć w naszych codziennych zadaniach kodowania.

W tej sekcji zaktualizowałem również kod odwiedzającego, aby odwiedzić każdy węzeł w tym drzewie wyrażeń i zapisać informacje o węzłach utworzonych w tym przykładzie. Przykładowy kod można [wyświetlić lub pobrać w](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) repozytorium GitHub dotnet/docs. Eksperymentuj dla siebie, budując i uruchamiając próbki. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Badanie interfejsów API

Interfejsy API drzewa wyrażeń są jednymi z trudniejszych do nawigowania w .NET Core, ale to dobrze. Ich celem jest dość złożone przedsięwzięcie: pisanie kodu, który generuje kod w czasie wykonywania. Są one koniecznie skomplikowane, aby zapewnić równowagę między obsługą wszystkich struktur kontroli dostępnych w języku Języka C# i utrzymanie powierzchni interfejsów API tak małe, jak uzasadnione. Ta równowaga oznacza, że wiele struktur kontroli są reprezentowane nie przez ich konstrukcje C#, ale przez konstrukcje, które reprezentują logikę podstawową, że kompilator generuje z tych konstrukcji wyższego poziomu.

Ponadto w tej chwili istnieją wyrażenia C#, które `Expression` nie mogą być budowane bezpośrednio przy użyciu metod klasy. Ogólnie rzecz biorąc będą to najnowsze operatory i wyrażenia dodane w językach C# 5 i C# 6. (Na przykład `async` wyrażenia nie mogą być `?.` budowane i nie można bezpośrednio utworzyć nowego operatora).

[Dalej - Tłumaczenie wyrażeń](expression-trees-translating.md)
