---
title: Wykonywanie drzew wyrażeń
description: Dowiedz się więcej o wykonywaniu drzew wyrażeń, konwertując je na instrukcje IL (wykonywalny język pośredni).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 802a83f52f9c05a99c3f49f8f6511eff81ef3eaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146024"
---
# <a name="executing-expression-trees"></a>Wykonywanie drzew wyrażeń

[Poprzedni -- Typy struktury obsługujące drzewa wyrażeń](expression-classes.md)

*Drzewo wyrażeń* jest strukturą danych, która reprezentuje jakiś kod.
Nie jest skompilowany i wykonywalny kod. Jeśli chcesz wykonać kod .NET, który jest reprezentowany przez drzewo wyrażeń, należy przekonwertować go na wykonywalne instrukcje IL.

## <a name="lambda-expressions-to-functions"></a>Wyrażenia Lambda do funkcji

Można przekonwertować dowolny LambdaExpression lub dowolny typ pochodzący z LambdaExpression do pliku wykonywalnego IL. Nie można bezpośrednio przekonwertować innych typów wyrażeń na kod. Ograniczenie to ma niewielki wpływ w praktyce. Wyrażenia Lambda są jedynymi typami wyrażeń, które chcesz wykonać, konwertując na wykonywalny język pośredni (IL). (Zastanów się, co to `ConstantExpression`znaczy bezpośrednio wykonać . Czy oznaczałoby to coś użytecznego?) Każde drzewo `LambdaExpression`wyrażeń, które jest `LambdaExpression` , lub typu pochodzącego z mogą być konwertowane na IL.
Typ `Expression<TDelegate>` wyrażenia jest jedynym konkretnym przykładem w bibliotekach .NET Core. Jest on używany do reprezentowania wyrażenia, które mapuje do dowolnego typu delegata. Ponieważ ten typ jest mapowany na typ delegata, program .NET może sprawdzić wyrażenie i wygenerować il dla odpowiedniego delegata, który pasuje do podpisu wyrażenia lambda.

W większości przypadków tworzy to proste mapowanie między wyrażeniem i jego odpowiedniego delegata. Na przykład drzewo wyrażeń, `Expression<Func<int>>` które jest reprezentowane przez zostanie `Func<int>`przekonwertowany na delegata typu . Dla wyrażenia lambda z dowolnego typu zwracanego i listy argumentów istnieje typ delegata, który jest typem docelowym dla kodu wykonywalnego reprezentowanego przez to wyrażenie lambda.

Typ `LambdaExpression` zawiera `Compile` `CompileToMethod` i elementy członkowskie, które można użyć do konwersji drzewa wyrażeń do kodu wykonywalnego. Metoda `Compile` tworzy delegata. Metoda `CompileToMethod` aktualizuje `MethodBuilder` obiekt za pomocą IL, który reprezentuje skompilowane dane wyjściowe drzewa wyrażeń. Należy `CompileToMethod` zauważyć, że jest dostępna tylko w pełnej struktury pulpitu, a nie w .NET Core.

Opcjonalnie można również `DebugInfoGenerator` podać, który otrzyma informacje o debugowaniu symbolu dla wygenerowanego obiektu delegata. Dzięki temu można przekonwertować drzewo wyrażeń do obiektu delegata i mieć pełne informacje debugowania o wygenerowanym pełnomocnika.

Wyrażenie można przekonwertować na pełnomocnika przy użyciu następującego kodu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Należy zauważyć, że typ delegata jest oparty na typie wyrażenia. Musisz znać typ zwracany i listę argumentów, jeśli chcesz użyć obiektu delegata w sposób silnie typowany. Metoda `LambdaExpression.Compile()` zwraca `Delegate` typ. Należy rzutować go do prawidłowego typu delegata, aby wszelkie narzędzia czasu kompilacji sprawdzić listę argumentów lub typ zwracany.

## <a name="execution-and-lifetimes"></a>Wykonanie i okresy istnienia

Kod można wykonać, wywołując pełnomocnika utworzonego `LambdaExpression.Compile()`po wywołaniu . Możesz zobaczyć powyższe, gdzie `add.Compile()` zwraca delegata. Wywoływanie tego delegata, `func()` wywołując wykonuje kod.

Ten delegat reprezentuje kod w drzewie wyrażeń. Można zachować dojście do tego pełnomocnika i wywołać go później. Nie trzeba kompilować drzewa wyrażeń za każdym razem, gdy chcesz wykonać kod, który reprezentuje. (Pamiętaj, że drzewa wyrażeń są niezmienne, a kompilacja tego samego drzewa wyrażeń później utworzy pełnomocnika, który wykonuje ten sam kod).

Przestrzegę przed próbami tworzenia bardziej zaawansowanych mechanizmów buforowania w celu zwiększenia wydajności, unikając niepotrzebnych wywołań kompilacji. Porównanie dwóch drzew wyrażeń dowolnego, aby ustalić, czy reprezentują one ten sam algorytm będzie również czasochłonne do wykonania. Prawdopodobnie okaże się, że czas obliczeniowy można zapisać `LambdaExpression.Compile()` unikając żadnych dodatkowych wywołań będzie więcej niż zużyte przez czas wykonywania kodu, który określa dwa różne drzewa wyrażeń spowodować ten sam kod wykonywalny.

## <a name="caveats"></a>Zastrzeżenia

Kompilowanie wyrażenia lambda do delegata i wywoływanie tego delegata jest jedną z najprostszych operacji, które można wykonać za pomocą drzewa wyrażeń. Jednak nawet przy tej prostej operacji istnieją zastrzeżenia, o których musisz wiedzieć.

Wyrażenia Lambda utworzyć zamknięcia nad dowolnymi zmiennymi lokalnymi, które są przywoływani w wyrażeniu. Należy zagwarantować, że wszystkie zmienne, które byłyby częścią delegata są `Compile`użyteczne w lokalizacji, w której wywołasz , i podczas wykonywania wynikowego delegata.

Ogólnie rzecz biorąc kompilator zapewni, że jest to prawda. Jednak jeśli wyrażenie uzyskuje dostęp do `IDisposable`zmiennej, która implementuje , jest możliwe, że kod może usunąć obiektu, gdy jest nadal w posiadaniu drzewa wyrażeń.

Na przykład ten kod działa `int` dobrze, `IDisposable`ponieważ nie implementuje:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Pełnomocnik przechwycił odwołanie do zmiennej `constant`lokalnej .
Ta zmienna jest dostępna w dowolnym momencie później, gdy funkcja zwracana przez `CreateBoundFunc` executes.

Należy jednak wziąć pod uwagę tę (raczej `IDisposable`wymyśloną) klasę, która implementuje:

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

Jeśli używasz go w wyrażeniu, jak `ObjectDisposedException` pokazano poniżej, otrzymasz po `Resource.Argument` wykonaniu kodu, do którego odwołuje się właściwość:

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

Delegat zwrócony z tej metody został `constant` zamknięty nad obiektem, który został usunięty. (Został usunięty, ponieważ został zadeklarowany w `using` oświadczeniu).)

Teraz po wykonaniu pełnomocnika zwrócone z tej metody, `ObjectDisposedException` będziesz miał wygenerowany w punkcie wykonania.

Wydaje się dziwne, że błąd wykonywania reprezentującykompilacji kompilacji czas, ale to jest świat, który wchodzimy podczas pracy z drzewa wyrażeń.

Istnieje wiele permutacji tego problemu, więc trudno jest zaoferować ogólne wskazówki, aby go uniknąć. Należy zachować ostrożność podczas uzyskiwania dostępu do zmiennych lokalnych podczas definiowania wyrażeń i należy zachować ostrożność podczas uzyskiwania dostępu do stanu w bieżącym obiekcie (reprezentowany przez `this`) podczas tworzenia drzewa wyrażeń, które mogą być zwracane przez publiczny interfejs API.

Kod w wyrażeniu może odwoływać się do metod lub właściwości w innych zestawach. Ten zestaw musi być dostępny, gdy wyrażenie jest zdefiniowane i gdy jest kompilowany i gdy wynikowy delegat jest wywoływany. Spotkasz się z `ReferencedAssemblyNotFoundException` w przypadkach, gdy nie jest obecny.

## <a name="summary"></a>Podsumowanie

Drzewa wyrażeń reprezentujące wyrażenia lambda można skompilować w celu utworzenia pełnomocnika, który można wykonać. Zapewnia to jeden mechanizm do wykonania kodu reprezentowanego przez drzewo wyrażeń.

Drzewo wyrażeń reprezentuje kod, który będzie wykonywany dla dowolnej konstrukcji, którą tworzysz. Tak długo, jak środowisko, w którym skompilować i wykonać kod pasuje do środowiska, w którym można utworzyć wyrażenie, wszystko działa zgodnie z oczekiwaniami. Jeśli tak się nie stanie, błędy są bardzo przewidywalne i zostaną one przechwycone w pierwszych testach dowolnego kodu przy użyciu drzew wyrażeń.

[Dalej - Interpretacja wyrażeń](expression-trees-interpreting.md)
