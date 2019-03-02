---
title: Wykonywanie drzew wyrażeń
description: Więcej informacji na temat wykonywanie drzew wyrażeń, konwertując je do pliku wykonywalnego instrukcje języka pośredniego (IL).
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: f6dca5a3965924e8eb6e1c04fe7ffc3c78c7df93
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201849"
---
# <a name="executing-expression-trees"></a>Wykonywanie drzew wyrażeń

[Poprzednie — Typy platform obsługujące drzewa wyrażeń](expression-classes.md)

*Drzewa wyrażeń* to struktura danych, który reprezentuje kodu.
Nie jest skompilowany i wykonywalnego kodu. Do wykonania kodu platformy .NET, który jest reprezentowany przez drzewo wyrażenia, należy ją przekonwertować do pliku wykonywalnego instrukcje języka IL.

## <a name="lambda-expressions-to-functions"></a>Wyrażenia lambda do funkcji

Możesz również przekonwertować wszystkie Wyrażenielambda lub dowolnego typu opracowane z Wyrażenielambda do pliku wykonywalnego IL. Inne typy wyrażenia nie można przekonwertować bezpośrednio w kodzie. Ograniczenie to ma niewielki wpływ w praktyce. Wyrażenia lambda są tylko typy wyrażeń, które trzeba będzie wykonać za pomocą konwersji do pliku wykonywalnego języka pośredniego (IL). (Myśl o tym, na co oznaczałoby bezpośrednie wykonywanie `ConstantExpression`. Może to oznaczać żadnych użytecznych?) Wszelkie drzewa wyrażeń, który jest `LambdaExpression`, lub typ pochodzący od `LambdaExpression` mogą być konwertowane na IL.
Typ wyrażenia `Expression<TDelegate>` tylko konkretnych przykład w bibliotekach .NET Core. Jest ona używana do reprezentowania wyrażenia, który jest mapowany do dowolnego typu delegata. Ponieważ ten typ jest mapowany do typu delegata, .NET można zbadać wyrażenie i wygenerować IL dla odpowiednich delegata, który pasuje do podpisu wyrażenia lambda. 

W większości przypadków spowoduje to utworzenie mapowania proste między wyrażenia oraz jego odpowiednie delegata. Na przykład drzewo wyrażenia, który jest reprezentowany przez `Expression<Func<int>>` zostanie przekonwertowana na delegata tego typu `Func<int>`. Dla wyrażenia lambda z listy argumentów i zwracanego typu istnieje typ delegata, który jest typem docelowym dla pliku wykonywalnego kodu, reprezentowane przez to wyrażenie lambda.

`LambdaExpression` Typ zawiera `Compile` i `CompileToMethod` elementów członkowskich, które umożliwiają przekonwertować drzewa wyrażenie kodu wykonywalnego. `Compile` Metoda tworzy delegata. `CompileToMethod` Metody aktualizacji `MethodBuilder` obiektu IL, reprezentujący skompilowanych danych wyjściowych drzewa wyrażeń. Należy pamiętać, że `CompileToMethod` dostępną tylko w ramach całego pulpitu, a nie w .NET Core.

Opcjonalnie możesz też podać `DebugInfoGenerator` , zostanie wyświetlony symbol informacji debugowania dla obiektu delegowanego wygenerowany. Dzięki temu można przekonwertować na drzewo wyrażenia do obiektu delegowanego i mają pełne informacje debugowania o wygenerowanym delegata.

Wyrażenie może przekonwertować na obiekt delegowany, używając następującego kodu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Należy zauważyć, że typ delegata jest oparty na typ wyrażenia. Jeśli chcesz użyć obiektu delegowanego w silnie typizowany sposób musisz znać typ zwracany i listą argumentów. `LambdaExpression.Compile()` Metoda zwraca `Delegate` typu. Będzie trzeba go rzutować na typ delegata poprawne mieć żadnych narzędzi kompilacji, zapoznaj się z listą argument lub zwracany typ.

## <a name="execution-and-lifetimes"></a>Okresy istnienia i wykonywanie

Wykonywania kodu za pomocą wywołania delegata utworzone podczas wywołania `LambdaExpression.Compile()`. Widać to powyżej gdzie `add.Compile()` zwraca delegata. Wywołanie delegata, wywołując `func()` wykonuje kod.

Ten delegat reprezentuje kod w drzewie wyrażeń. Można zachować dojścia do delegata i wywoływać go później. Nie musisz skompilować każdorazowo, którą chcesz wykonywać kod, który reprezentuje drzewo wyrażenia. (Należy pamiętać, że drzew wyrażeń są niezmienne i kompilowanie później tego samego drzewa wyrażeń utworzy obiekt delegowany, który jest wykonywany ten sam kod).

I będzie przestrzega przed w trakcie tworzenia jakichkolwiek bardziej zaawansowanych mechanizmów buforowania, co pozwoli zwiększyć wydajność przez unikanie niepotrzebnych kompilacji wywołania. Porównywanie dwa drzewa wykonania dowolnego wyrażenia, aby określić, czy stanowią one ten sam algorytm będzie również dużo czasu do wykonania. Prawdopodobnie okaże czas obliczeń zapisanie unikanie wszelkie dodatkowe wywołania `LambdaExpression.Compile()` będzie możliwe więcej niż przez czas wykonywania kodu, który określa dwóch różnych drzew wyrażeń spowodować tego samego kodu wykonywalnego.

## <a name="caveats"></a>Ostrzeżenia

Kompilowanie wyrażenia lambda do delegata i wywoływania delegata jest jednym z najprostszym operacje, które można wykonywać na drzewo wyrażenia. Jednak nawet w przypadku tej operacji proste, istnieją zastrzeżenia, których należy wiedzieć. 

Wyrażenia lambda Utwórz wolnych od pracy nad zmienne lokalne, które są przywoływane w wyrażeniu. Musisz gwarantować, wszystkie zmienne, które są częścią obiektu delegowanego jest użyteczne w lokalizacji, gdzie jest wywoływana `Compile`, a podczas wykonywania wynikowego delegata.

Ogólnie rzecz biorąc kompilator zapewnia, że ta zasada obowiązuje. Jednakże jeśli wyrażenie uzyskuje dostęp do zmiennej, która implementuje `IDisposable`, istnieje możliwość, że Twój kod może usunąć obiekt podczas nadal odbywa się przez drzewa wyrażeń.

Na przykład, ten kod działa poprawnie, ponieważ `int` nie implementuje `IDisposable`:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Delegat został przechwycony odwołaniem do zmiennej lokalnej `constant`.
Tej zmiennej jest dostępna w dowolnym momencie później, po wartość zwrócona przez funkcję przez `CreateBoundFunc` wykonuje.

Jednak wziąć pod uwagę tej klasy (zamiast contrived), który implementuje `IDisposable`:

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

Jeśli jest ona używana w wyrażeniu jak pokazano poniżej, otrzymasz `ObjectDisposedException` podczas wykonywania kodu, odwołuje się `Resource.Argument` właściwości:

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

Delegat zwrócone w wyniku tej metody został zamknięty przez `constant` obiektu, który został zlikwidowany. (Jest został usunięty, ponieważ została ona zadeklarowana w `using` instrukcja.) 

Teraz, po wykonaniu delegata zwrócone w wyniku tej metody, będziesz mieć `ObjectDisposedException` generowany w momencie wykonywania.

Wydawać się dziwne mają reprezentujących konstrukcję kompilacji błąd w czasie wykonywania, ale jest to świecie, w którym możemy wprowadzić, kiedy będziemy pracować z drzewa wyrażeń.

Dlatego jest trudny do oferty ogólne wskazówki, aby uniknąć tego błędu jest dostępnych wiele permutacji tego problemu. Należy zachować ostrożność podczas definiowania wyrażeń uzyskiwania dostępu do zmiennych lokalnych i należy zachować ostrożność w przypadku uzyskiwania dostępu do stanu w bieżącym obiekcie (reprezentowane przez `this`) podczas tworzenia drzewa wyrażenie, które mogą być zwrócone przez publiczny interfejs API.

Kod w swoim wyrażeniu może odwoływać się do metody lub właściwości w innych zestawach. Ten zestaw musi być dostępny, gdy wyrażenie jest zdefiniowany i gdy jest ona kompilowana i kiedy wynikowy obiekt delegowany jest wywoływany. Można będzie spełniony przy użyciu `ReferencedAssemblyNotFoundException` w przypadkach, gdy nie jest obecny.

## <a name="summary"></a>Podsumowanie

Drzewa wyrażeń, które reprezentują wyrażenia lambda może być kompilowane do utworzenia delegata, który może zostać uruchomiony. Zapewnia jeden mechanizm, aby wykonać ten kod reprezentowany przez drzewo wyrażenia.

Drzewo wyrażenia reprezentuje kod, który jest wykonywany dla danego konstrukcji, które można utworzyć. Tak długo, jak środowisko, gdzie skompilować i wykonać ten kod jest zgodny z środowisku, w którym są tworzone wyrażenie, wszystko działa zgodnie z oczekiwaniami. Jeśli nie mają miejsce, błędy są bardzo przewidywalny i zostanie przechwycony w testach pierwszy dowolnego kodu, przy użyciu drzewa wyrażeń.

[Dalej — Interpretowanie wyrażeń](expression-trees-interpreting.md)
