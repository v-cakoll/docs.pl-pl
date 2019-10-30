---
title: Kompilowanie drzew wyrażeń
description: Dowiedz się więcej na temat technik tworzenia drzew wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 45628b00633c8d6ff51dbd5f5dbdda7ca25dd7c4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037091"
---
# <a name="building-expression-trees"></a>Kompilowanie drzew wyrażeń

[Wyrażenia z poprzednią interpretacją](expression-trees-interpreting.md)

Wszystkie drzewa wyrażeń, które były już widoczne, zostały utworzone przez C# kompilator. Przede wszystkim należało utworzyć wyrażenie lambda, które zostało przypisane do zmiennej wpisanej jako `Expression<Func<T>>` lub innego typu podobnego. Nie jest to jedyna metoda tworzenia drzewa wyrażenia. W przypadku wielu scenariuszy może się okazać, że trzeba utworzyć wyrażenie w pamięci w czasie wykonywania. 

Kompilowanie drzew wyrażeń jest skomplikowane przez fakt, że te drzewa wyrażeń są niezmienne. Niezmienne oznacza, że należy skompilować drzewo od opuszcza do katalogu głównego. Interfejsy API, które będą używane do tworzenia drzew wyrażeń, odzwierciedlają ten fakt: metody, które będą używane do kompilowania węzła, przyjmują wszystkie jego elementy podrzędne jako argumenty. Przechodźmy kilka przykładów, aby wyświetlić te techniki.

## <a name="creating-nodes"></a>Tworzenie węzłów

Zacznijmy od samego siebie. Użyjemy wyrażenia dodawania, z którym pracujemy w tych sekcjach:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Aby skonstruować to drzewo wyrażenia, należy skonstruować węzły liścia.
Węzły liścia są stałymi, więc można użyć metody `Expression.Constant`, aby utworzyć węzły:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Następnie utworzysz wyrażenie dodawania:

```csharp
var addition = Expression.Add(one, two);
```

Po otrzymaniu wyrażenia dodania można utworzyć wyrażenie lambda:

```csharp
var lambda = Expression.Lambda(addition);
```

Jest to bardzo proste wyrażenie lambda, ponieważ nie zawiera żadnych argumentów.
W dalszej części tej sekcji zobaczysz sposób mapowania argumentów na parametry i tworzenia bardziej skomplikowanych wyrażeń.

W przypadku wyrażeń, które są tak proste, można połączyć wszystkie wywołania w pojedynczą instrukcję:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Kompilowanie drzewa

Jest to podstawą tworzenia drzewa wyrażenia w pamięci. Bardziej złożone drzewa zwykle oznaczają więcej typów węzłów i więcej węzłów w drzewie. Zacznijmy od jednego przykładu i pokażę dwa typy węzłów, które zwykle utworzysz podczas tworzenia drzew wyrażeń: węzły argumentów i węzły wywołania metody.

Skompilujmy drzewo wyrażenia, aby utworzyć to wyrażenie:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Zacznij od utworzenia wyrażeń parametrów dla `x` i `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Tworzenie wyrażeń mnożenia i dodawania następuje po wzorcu, który był już widoczny:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Następnie należy utworzyć wyrażenie wywołania metody dla wywołania do `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

A następnie na końcu należy umieścić wywołanie metody w wyrażeniu lambda i upewnić się, że argumenty mają być zdefiniowane w wyrażeniu lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

W tym bardziej skomplikowanym przykładzie widać kilka dodatkowych technik, które często są potrzebne do tworzenia drzew wyrażeń.

Najpierw należy utworzyć obiekty, które reprezentują parametry lub zmienne lokalne przed ich użyciem. Po utworzeniu tych obiektów możesz użyć ich w drzewie wyrażenia wszędzie tam, gdzie jest to potrzebne.

Następnie należy użyć podzestawu interfejsów API odbicia do utworzenia obiektu `MethodInfo`, aby można było utworzyć drzewo wyrażenia, aby uzyskać dostęp do tej metody. Musisz ograniczyć się do podzbioru interfejsów API odbicia, które są dostępne na platformie .NET Core. Te techniki zostaną rozbudowane do innych drzew wyrażeń.

## <a name="building-code-in-depth"></a>Kompilowanie kodu na głębokość

Nie masz ograniczeń, co można skompilować za pomocą tych interfejsów API. Jednak bardziej skomplikowane drzewo wyrażeń, które chcesz skompilować, trudniejsze jest, aby kod był zarządzany i odczytywany. 

Utwórzmy drzewo wyrażenia, które jest odpowiednikiem tego kodu:

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

Zwróć uwagę na to, że drzewo wyrażenia nie zostało skompilowane, ale po prostu delegat. Przy użyciu klasy `Expression` nie można kompilować instrukcji lambda. Oto kod, który jest wymagany do skompilowania tych samych funkcji. Jest to skomplikowane przez fakt, że nie istnieje interfejs API do kompilowania pętli `while`, zamiast tego należy utworzyć pętlę zawierającą test warunkowy i miejsce docelowe etykiety, aby przerwać pętlę. 

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

Kod służący do kompilowania drzewa wyrażeń dla funkcji silniej jest zbyt długi, bardziej skomplikowany i jest riddled przy użyciu etykiet i instrukcji break oraz innych elementów, które chcemy uniknąć w naszych codziennych zadaniach kodowania. 

W tej sekcji Zaktualizowaliśmy również kod gościa, aby odwiedzić każdy węzeł w tym drzewie wyrażenia i napisać informacje o węzłach, które zostały utworzone w tym przykładzie. Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) w repozytorium GitHub/docs w serwisie. Wypróbuj samodzielnie, kompilując i uruchamiając próbki. Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Badanie interfejsów API

Interfejsy API drzewa wyrażeń są trudniejsze do nawigowania w programie .NET Core, ale jest to odpowiednie. Ich celem jest raczej złożone zobowiązanie: pisanie kodu, który generuje kod w czasie wykonywania. Są one koniecznie skomplikowane, aby zapewnić równowagę między obsługą wszystkich struktur kontroli dostępnych w C# języku i utrzymywaniem obszaru powierzchni interfejsów API w niewielkim sensie. To saldo oznacza, że wiele struktur kontroli nie jest przedstawianych przez ich C# konstrukcje, ale przez konstrukcje, które reprezentują podstawową logikę wygenerowaną przez kompilator z tych konstrukcji wyższego poziomu. 

Ponadto w tym momencie istnieją C# wyrażenia, które nie mogą być kompilowane bezpośrednio przy użyciu metod klasy`Expression`. Ogólnie rzecz biorąc, są to najnowsze operatory i wyrażenia dodane w C# 5 i C# 6. (Na przykład wyrażenia `async` nie mogą być kompilowane i nie można bezpośrednio utworzyć operatora `?.`).

[Następne--tłumaczenie wyrażeń](expression-trees-translating.md)
