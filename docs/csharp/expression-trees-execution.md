---
title: "Wykonywanie drzew wyrażeń"
description: "Więcej informacji na temat wykonywanie drzew wyrażeń konwertując je do pliku wykonywalnego instrukcje języku pośrednim (IL)."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: db481c18a79f55b079ec2558b884ce288e2a9933
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="executing-expression-trees"></a>Wykonywanie drzew wyrażeń

[Poprzednie — Framework typy obsługi drzewa wyrażeń](expression-classes.md)

*Drzewo wyrażeń* jest strukturą danych, która reprezentuje kod.
Nie jest skompilowany i wykonywalnego kodu. Jeśli chcesz wykonać kodu platformy .NET, reprezentowanym przez wyrażenie drzewa musi przekształcać je do pliku wykonywalnego instrukcji IL. 
## <a name="lambda-expressions-to-functions"></a>Wyrażenia lambda na funkcje
Możesz przekonwertować wszystkie LambdaExpression lub dowolny typ pochodny LambdaExpression do pliku wykonywalnego IL. Inne typy wyrażeń nie można przekonwertować bezpośrednio w kodzie. Ograniczenie to ma niewielki wpływ, w praktyce. Wyrażenia lambda są tylko typy wyrażeń, które chcesz wykonać konwersję na język pośredni pliku wykonywalnego (IL). (Pomyśl o jakie oznaczałoby to wykonać bezpośrednio `ConstantExpression`. Może to oznaczać niczego przydatne?) Wszelkie drzewo wyrażeń, który jest `LamdbaExpression`, lub typ pochodzący od `LambdaExpression` może zostać przekonwertowany na IL.
Typ wyrażenia `Expression<TDelegate>` tylko konkretnych przykład w bibliotekach .NET Core. Jest ona używana do reprezentowania wyrażenia mapujący do dowolnego typu delegowanego. Ponieważ mapuje ten typ do typu delegata, .NET można zbadać wyrażenie i generowanie IL dla odpowiednich delegata, który pasuje do podpisu wyrażenia lambda. 

W większości przypadków spowoduje to utworzenie prostego mapowanie między wyrażenia i jego odpowiedniego obiektu delegowanego. Na przykład drzewo wyrażenia, który jest reprezentowany przez `Expression<Func<int>>` zostanie przekonwertowana na delegata typu `Func<int>`. Wyrażenia lambda z zwracany typ i listy argumentów istnieje typ delegata, który typ docelowy dla kodu wykonywalnego reprezentowany przez tego wyrażenia lamdba.

`LamdbaExpression` Typ zawiera `Compile` i `CompileToMethod` elementów członkowskich, które należy użyć, aby przekonwertować kod wykonywalny drzewo wyrażenia. `Compile` Metoda tworzy delegata. `CompileToMethod` Aktualizacje metody `MethodBuilder` obiektu IL, reprezentujący skompilowanych danych wyjściowych drzewa wyrażenia. Należy pamiętać, że `CompileToMethod` znajduje się tylko w ramach całego pulpitu, a nie na platformę .NET Core.

Opcjonalnie można też podać `DebugInfoGenerator` który otrzyma symbol informacji debugowania dla obiekt wygenerowanego obiektu delegowanego. Dzięki temu można ich przekonwertować na obiekt delegowany drzewa wyrażenia oraz pełne informacje o debugowaniu o wygenerowanego obiektu delegowanego.

Czy przekonwertować wyrażenia na delegata, używając następującego kodu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Zwróć uwagę, że typ delegata jest oparty na typie wyrażenia. Zwracany typ i listy argumentów musi sprawdzić, czy ma być używany w sposób jednoznaczny obiektu delegowanego. `LambdaExpression.Compile()` Metoda zwraca `Delegate` typu. Należy rzutować go na typ delegata poprawne mieć żadnych narzędzi kompilacji, zapoznaj się z listą argumentów typu zwracanego.

## <a name="execution-and-lifetimes"></a>Wykonanie i okresy istnienia

Wykonanie kodu za pomocą delegowanego utworzony podczas wywołania `LamdbaExpression.Compile()`. Widać to powyżej where `add.Compile()` zwraca delegata. Wywoływanie tego delegata, wywołując `func()` wykonuje kod.

Ten delegat reprezentuje kod w drzewa wyrażenia. Możesz zachować dojścia do tego obiektu delegowanego i wywołać go później. Nie trzeba było skompilować drzewa wyrażenia zawsze będzie wykonywany kod, który reprezentuje. (Pamiętać, że drzew wyrażeń są niezmienne i później kompilowanie tym samym drzewie wyrażenie utworzy delegata, który wykonuje ten sam kod.)

Zostanie I uwaga przed w trakcie tworzenia jakichkolwiek bardziej zaawansowanych mechanizmów buforowania w celu zwiększenia wydajności dzięki unikaniu kompilacji niepotrzebne wywołania. Porównanie dwóch drzew wyrażeń dowolnego, aby ustalić, czy reprezentują ten sam algorytm będzie również dużo czasu na wykonanie. Prawdopodobnie znajdziesz czasu obliczeniowego zapisanie unikanie wszelkie dodatkowe wywołania `LambdaExpression.Compile()` zostaną użyte więcej niż w czasie wykonywania kod, który określa dwóch różnych drzewach wyrażeń spowodować tego samego kodu wykonywalnego.

## <a name="caveats"></a>Ostrzeżenia

Kompilowanie wyrażenia lambda do delegata i wywoływanie ten delegat jest jednym z najprostszym operacje, które można wykonywać na drzewo wyrażenia. Nawet w przypadku tej operacji proste, istnieją ostrzeżenia, który musi być znane. 

Wyrażenia lambda utworzyć zamknięcia przez wszystkie zmienne lokalne, których istnieją odwołania w wyrażeniu. Musi gwarantuje, że wszystkie zmienne, które są częścią delegata są użyteczne, w lokalizacji, w którym należy wywołać `Compile`, a podczas wykonywania wynikowy delegata.

Ogólnie rzecz biorąc kompilator zagwarantować, że jest to true. Jednak jeśli w wyrażeniu uzyskuje dostęp do zmiennej, która implementuje `IDisposable`, istnieje możliwość, że kodu może zlikwidować obiektu podczas, gdy nadal jest przechowywany przez drzewa wyrażenia.

Na przykład ten kod działa prawidłowo, ponieważ `int` nie implementuje `IDisposable`:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Delegat zostały przechwycone odwołanie do zmiennej lokalnej `constant`.
Tej zmiennej jest dostępny w dowolnym momencie później, gdy wartość zwrócona przez funkcję przez `CreateBoundFunc` wykonuje.

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

Jeśli można go użyć w wyrażeniu w sposób przedstawiony poniżej, otrzymasz `ObjectDisposedException` podczas wykonywania kodu odwołuje się `Resource.Argument` właściwości:

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

Delegat zwracane z tej metody został zamknięty przez `constant` obiektu, który został zlikwidowany. (Jest został usunięty, ponieważ zostało zadeklarowane w `using` instrukcji.) 

Teraz, po wykonaniu delegata zwracane z tej metody należy `ObjecctDisposedException` zgłoszony w punkcie wykonywania.

Wydawać się dziwne błąd środowiska uruchomieniowego reprezentujący konstrukcję kompilacji, ale jest to world, którego możemy wprowadzić podczas współpracy z drzewa wyrażeń.

Istnieje wiele permutacji ten problem, tak trudno oferują ogólne wskazówki, aby uniknąć tego problemu. Należy zachować ostrożność podczas uzyskiwania dostępu do zmiennych lokalnych podczas definiowania wyrażeń i należy zachować ostrożność podczas uzyskiwania dostępu do stanu w bieżącym obiekcie (reprezentowane przez `this`) podczas tworzenia drzewa wyrażeń, który może być zwracany przez publiczny interfejs API.

Kod w wyrażeniu mogą odwoływać się do metody lub właściwości w innych zestawów. Tego zestawu musi być dostępny, gdy zdefiniowano wyrażenia i gdy jest on skompilowany i po wywołaniu wynikowy delegata. Będzie spełnienia z `ReferencedAssemblyNotFoundException` w przypadkach, gdy nie jest obecny.

## <a name="summary"></a>Podsumowanie

Drzewa wyrażeń, które reprezentują wyrażenia lambda, może zostać skompilowany do utworzenia delegata, który może zostać uruchomiony. Zapewnia jeden mechanizm można wykonać kod reprezentowany przez drzewo wyrażenia.

Drzewo wyrażenia reprezentuje kod, który jest wykonywany dla danego konstrukcji utworzone. Tak długo, jak środowisko, gdzie skompilować i wykonywania kodu zgodne środowisko, w której utworzono wyrażenie, wszystko działa zgodnie z oczekiwaniami. Gdy które się nie stało, błędy są bardzo przewidywalne i zostanie przechwycony w pierwszym testów dowolnego kodu przy użyciu drzewa wyrażeń.

[Dalej — Interpretowanie wyrażenia](expression-trees-interpreting.md)
