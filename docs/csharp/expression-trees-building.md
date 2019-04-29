---
title: Tworzenie drzew wyrażeń
description: Dowiedz się więcej o technikach tworzenia drzew wyrażeń.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7751af17aafa8e2d1a14125da43352108b1c1f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646601"
---
# <a name="building-expression-trees"></a>Tworzenie drzew wyrażeń

[Poprzednie — Interpretowanie wyrażeń](expression-trees-interpreting.md)

Drzewa wyrażeń w tym samouczku do tej pory zostały utworzone przez C# kompilatora. Wszystkie trzeba było robić zostały, utwórz wyrażenie lambda, która została przypisana do zmiennych wpisanych w formie `Expression<Func<T>>` lub podobne typu. To nie jest jedynym sposobem, aby utworzyć drzewo wyrażenia. Umożliwia obsługę wielu scenariuszy może się okazać, że potrzebne do tworzenia wyrażenia w pamięci w czasie wykonywania. 

Tworzenie drzew wyrażeń jest skomplikowane faktem, że te drzew wyrażeń są niezmienne. Trwa niezmienne oznacza, że utworzenie drzewa liści do katalogu głównego. Interfejsy API, które będą używane do tworzenia drzew wyrażeń odzwierciedla fakt: Metody, które będą używane do tworzenia węzła podjąć wszystkie jego elementy podrzędne jako argumenty. Przejdźmy przez kilka przykładów, aby pokazać Ci te techniki.

## <a name="creating-nodes"></a>Tworzenie węzłów

Zacznijmy od stosunkowo po prostu ponownie. Użyjemy dodawania wprowadzone wyrażenie I masz doświadczenie w pracy z całym następujące sekcje:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Do konstruowania takiego drzewa wyrażeń, należy tworzyć węzły liści.
Węzły liści są stałe, aby można było używać `Expression.Constant` metodę w celu utworzenia węzłów:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Następnie utworzysz wyrażenie dodawania:

```csharp
var addition = Expression.Add(one, two);
```

Gdy już masz, aby wyrażenie dodawania, można utworzyć wyrażenie lambda:

```csharp
var lambda = Expression.Lambda(addition);
```

To wyrażenie lambda bardzo proste, ponieważ zawiera ona żadnych argumentów.
Później w tej sekcji pokazano, jak do mapowania argumentów do parametrów i tworzenie bardziej złożonych.

W wyrażeniach, które są proste, jak ta można połączyć wszystkie wywołania do pojedynczej instrukcji:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Tworzenie drzewa

To podstawy tworzenia drzewa wyrażeń w pamięci. Bardziej złożone drzewa zazwyczaj oznacza większą liczbę typów węzła i więcej węzłów w drzewie. Teraz uruchom za pomocą jednego więcej przykład i Pokaż dwa większą liczbę typów węzłów, które będą zwykle tworzysz podczas tworzenia drzew wyrażeń: argument węzłów i węzłów wywołania metody.

Utwórzmy drzewo wyrażenia, aby utworzyć to wyrażenie:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Użytkownik rozpoczyna się przez utworzenie parametr wyrażenia dla `x` i `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Tworzenie wyrażenia mnożenia i dodanie jest zgodna z wzorcem, został już wcześniej:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Następnie należy utworzyć metodę wyrażenie wywołania do wywołań `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

A następnie na końcu, Umieść wywołanie metody Wyrażenie lambda i upewnij się zdefiniować argumentów do wyrażenia lambda:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

W tym przykładzie bardziej skomplikowane widzisz kilka więcej technik, które często należy do tworzenia drzew wyrażeń.

Najpierw musisz utworzyć obiekty, które reprezentują parametry lub zmienne lokalne, przed ich użyciem. Po utworzeniu tych obiektów można ich używać w Twojej drzewa wyrażeń wszędzie tam, gdzie należy.

Po drugie, musisz użyć podzestawu interfejsów API odbicia do utworzenia `MethodInfo` obiekt, w którym można utworzyć drzewa wyrażenie na dostęp do tej metody. Trzeba ograniczać się do podzbioru interfejsów API odbicia, które są dostępne na platformie .NET Core. Ponownie techniki te będą dotyczyć innych drzew wyrażeń.

## <a name="building-code-in-depth"></a>Tworzenie kodu w głębi

Nie są ograniczone, w jakie możesz tworzyć zawartość przy użyciu tych interfejsów API. Jednak bardziej skomplikowane drzewa wyrażeń, który chcesz skompilować, tym trudniej kod jest do zarządzania i do odczytu. 

Utwórzmy drzewo wyrażenia, który jest odpowiednikiem tego kodu:

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

Zwróć uwagę, powyżej, czy nie skompilowano drzewa wyrażeń, ale po prostu delegata. Za pomocą `Expression` klasy, nie można przeprowadzić kompilacji lambdy instrukcji. Poniżej przedstawiono kod, który jest wymagany do kompilowania taką samą funkcjonalność. Jest to skomplikowane faktem, że nie ma interfejs API umożliwiający tworzenie `while` pętli, zamiast tego trzeba tworzyć pętli, który zawiera test warunkowy i cel etykiety, aby zerwać pętlę. 

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

Kod, aby zbudować drzewa wyrażeń silni funkcji jest dość to nieco dłużej, bardziej skomplikowane i jest on riddled z etykietami i instrukcji break i inne elementy, które firma Microsoft chce uniknąć w naszym codziennie kodowania zadań. 

W tej sekcji również po aktualizacji obiektu odwiedzającego kodu do odwiedzenia każdego węzła w tym drzewa wyrażeń i zapisać informacje o węzłach, które są tworzone w tym przykładzie. Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) w repozytorium dotnet/docs w witrynie GitHub. Poeksperymentuj samodzielnie, tworząc i uruchamianie przykładów programu. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Badanie interfejsów API

Drzewo wyrażenia interfejsy API są niektóre trudniejsze do nawigacji w programie .NET Core, ale jest dobrym rozwiązaniem. Ich celem jest raczej złożonych przedsiębiorstwa: pisanie kodu, który generuje kod w czasie wykonywania. Są one zawsze skomplikowane zapewnienie równowagi między Obsługa dostępne w struktur sterujących C# języka i utrzymywanie powierzchni interfejsów API niewielkie jako uzasadnione. Saldo to oznacza, że wielu struktur sterowania są reprezentowane nie przez ich C# konstrukcji, ale przez konstrukcji, które reprezentują podstawowej logiki, które kompilator generuje na podstawie tych wyższego poziomu konstrukcji. 

W tej chwili istnieje też C# wyrażeń, które nie może zostać utworzony bezpośrednio przy użyciu `Expression` metody klasy. Ogólnie rzecz biorąc, będą one najnowszych operatory i wyrażenia dodane w C# 5 i C# 6. (Na przykład `async` wyrażenia nie może być kompilowana, a nowe `?.` operator nie można bezpośrednio utworzyć.)

[Dalej — Translacja wyrażeń](expression-trees-translating.md)
