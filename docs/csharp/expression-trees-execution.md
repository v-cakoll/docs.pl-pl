---
title: Wykonywanie drzew wyrażeń
description: Dowiedz się więcej o wykonywaniu drzew wyrażeń, konwertując je na instrukcje wykonywalnego języka pośredniego (IL).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 9af4b346962cb743daddf774e8b3c1f8fa722ae4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037114"
---
# <a name="executing-expression-trees"></a>Wykonywanie drzew wyrażeń

[Poprzednie typy struktur obsługujące drzewa wyrażeń](expression-classes.md)

*Drzewo wyrażenia* jest strukturą danych, która reprezentuje kod.
Nie jest skompilowany i kod wykonywalny. Jeśli chcesz wykonać kod .NET, który jest reprezentowany przez drzewo wyrażenia, należy przekonwertować go na instrukcje pliku wykonywalnego IL.

## <a name="lambda-expressions-to-functions"></a>Wyrażenia lambda do funkcji

Można przekonwertować dowolne Wyrażenielambda lub dowolny typ pochodzący z Wyrażenielambda do pliku wykonywalnego IL. Inne typy wyrażeń nie mogą być bezpośrednio konwertowane na kod. To ograniczenie ma niewielki wpływ na praktyce. Wyrażenia lambda są jedynymi typami wyrażeń, które mają być wykonywane przez konwersję do wykonywalnego języka pośredniego (IL). (Należy zastanowić się, co będzie miało na celu bezpośrednie wykonanie `ConstantExpression`. Czy to oznacza coś przydatnego?) Dowolne drzewo wyrażeń, które jest `LambdaExpression`lub typ pochodzący od `LambdaExpression` można przekonwertować na IL.
Typ wyrażenia `Expression<TDelegate>` jest jedynym konkretnym przykładem w bibliotekach .NET Core. Służy do reprezentowania wyrażenia, które jest mapowane na dowolny typ delegata. Ponieważ ten typ jest mapowany na typ delegata, .NET może przeanalizować wyrażenie i wygenerować IL dla odpowiedniego delegata, który jest zgodny z podpisem wyrażenia lambda. 

W większości przypadków tworzy proste mapowanie między wyrażeniem i odpowiadającym mu delegatem. Na przykład drzewo wyrażenia, które jest reprezentowane przez `Expression<Func<int>>`, zostanie przekonwertowane na delegata typu `Func<int>`. W przypadku wyrażenia lambda z dowolnym typem zwracanym i listą argumentów istnieje typ delegata, który jest typem docelowym dla kodu wykonywalnego reprezentowanego przez to wyrażenie lambda.

Typ `LambdaExpression` zawiera `Compile` i `CompileToMethod` członków, których można użyć do przekonwertowania drzewa wyrażenia na kod wykonywalny. Metoda `Compile` tworzy delegata. Metoda `CompileToMethod` aktualizuje obiekt `MethodBuilder` z IL, który reprezentuje skompilowane dane wyjściowe drzewa wyrażenia. Należy pamiętać, że `CompileToMethod` jest dostępna tylko w pełnej strukturze pulpitu, a nie w środowisku .NET Core.

Opcjonalnie można również udostępnić `DebugInfoGenerator`, które będą otrzymywać informacje o debugowaniu symboli dla wygenerowanego obiektu delegowanego. Umożliwia to konwertowanie drzewa wyrażenia na obiekt delegata i zawiera pełne informacje o debugowaniu dotyczące wygenerowanego delegata.

Wyrażenie można przekonwertować na delegata przy użyciu następującego kodu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Należy zauważyć, że typ delegata jest oparty na typie wyrażenia. Musisz znać typ zwracany i listę argumentów, jeśli chcesz użyć obiektu delegata w sposób silnie wpisany. Metoda `LambdaExpression.Compile()` zwraca typ `Delegate`. Konieczne będzie przerzutowanie go do poprawnego typu delegata, aby wszystkie narzędzia czasu kompilacji sprawdzają listę argumentów lub typ zwracany.

## <a name="execution-and-lifetimes"></a>Wykonywanie i okresy istnienia

Kod jest wykonywany przez wywoływanie delegata utworzonego podczas wywoływania `LambdaExpression.Compile()`. Możesz zobaczyć powyższe miejsce, gdzie `add.Compile()` zwraca delegata. Wywoływanie tego delegata przez wywołanie `func()` wykonuje kod.

Ten delegat reprezentuje kod w drzewie wyrażenia. Możesz zachować uchwyt do tego delegata i wywołać go później. Nie musisz kompilować drzewa wyrażenia za każdym razem, gdy chcesz wykonać kod, który reprezentuje. (Należy pamiętać, że drzewa wyrażeń są niezmienne i skompilowanie tego samego drzewa wyrażeń później spowoduje utworzenie delegata, który wykonuje ten sam kod).

Będę mieć ostrożność w przypadku tworzenia bardziej zaawansowanych mechanizmów buforowania w celu zwiększenia wydajności poprzez uniknięcie niepotrzebnych wywołań kompilacji. Porównanie dwóch arbitralnych drzew wyrażeń w celu ustalenia, czy reprezentują one ten sam algorytm, również będzie czasochłonne wykonywanie operacji. Prawdopodobnie okaże się, że czas obliczeń, który zostanie zapisany, unikając jakichkolwiek dodatkowych wywołań `LambdaExpression.Compile()` będzie większy niż zużyty przez czas wykonywania kodu, który określa dwa różne drzewa wyrażeń wynik ten sam kod wykonywalny.

## <a name="caveats"></a>Zastrzeżenia

Kompilowanie wyrażenia lambda do delegata i wywoływanie tego delegata jest jedną z najprostszych operacji, które można wykonać za pomocą drzewa wyrażenia. Jednak nawet w przypadku tej prostej operacji istnieją zastrzeżenia, których należy wiedzieć. 

Wyrażenia lambda tworzą zamknięcia na wszystkich zmiennych lokalnych, do których istnieją odwołania w wyrażeniu. Należy zagwarantować, że wszystkie zmienne, które będą częścią delegata, są użyteczne w lokalizacji, w której jest wywoływana `Compile`, i po wykonaniu wyniku delegowanego.

Ogólnie rzecz biorąc, kompilator zapewni, że jest to prawdziwe. Jeśli jednak wyrażenie uzyskuje dostęp do zmiennej implementującej `IDisposable`, możliwe jest, że kod może usunąć obiekt, gdy nadal jest przechowywany w drzewie wyrażenia.

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

Delegat przechwycił odwołanie do zmiennej lokalnej `constant`.
Ta zmienna jest używana w dowolnym momencie później, gdy zostanie wykonana funkcja zwrócona przez `CreateBoundFunc`.

Należy jednak wziąć pod uwagę tę klasę (raczej contrived) implementującą `IDisposable`:

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

Jeśli używasz go w wyrażeniu, jak pokazano poniżej, uzyskasz `ObjectDisposedException` podczas wykonywania kodu, do którego odwołuje się Właściwość `Resource.Argument`:

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

Delegat zwrócony z tej metody został zamknięty przez obiekt `constant`, który został usunięty. (Element został usunięty, ponieważ został zadeklarowany w instrukcji `using`). 

Teraz po wykonaniu delegata zwróconego przez tę metodę będziesz mieć `ObjectDisposedException` zgłoszony w punkcie wykonywania.

Wydaje się, że wystąpił błąd środowiska uruchomieniowego reprezentujący konstrukcję w czasie kompilacji, ale jest to na świecie wprowadzanym podczas pracy z drzewami wyrażeń.

Istnieje wiele permutacji tego problemu, dlatego trudno jest zaoferować ogólne wskazówki, aby tego uniknąć. Pamiętaj o uzyskiwaniu dostępu do zmiennych lokalnych podczas definiowania wyrażeń i należy `this`zachować ostrożność podczas tworzenia drzewa wyrażenia, które może zostać zwrócone przez publiczny interfejs API.

Kod w wyrażeniu może odwoływać się do metod lub właściwości w innych zestawach. Ten zestaw musi być dostępny, gdy wyrażenie jest zdefiniowane, a kiedy jest kompilowane, oraz kiedy wywoływany jest otrzymany delegat. Zostanie osiągnięty `ReferencedAssemblyNotFoundException` w przypadkach, w których nie istnieje.

## <a name="summary"></a>Podsumowanie

Drzewa wyrażeń, które reprezentują wyrażenia lambda, można skompilować, aby utworzyć delegata, który można wykonać. Zapewnia to jeden mechanizm do wykonywania kodu reprezentowanego przez drzewo wyrażenia.

Drzewo wyrażenia reprezentuje kod, który będzie wykonywany dla każdej utworzonej konstrukcji. Tak długo, jak środowisko, w którym kompilujesz i wykonujesz kod, jest zgodne ze środowiskiem, w którym tworzysz wyrażenie, wszystko działa zgodnie z oczekiwaniami. Gdy tak się nie stanie, błędy są bardzo przewidywalne i zostaną przechwycone podczas pierwszych testów dowolnego kodu przy użyciu drzew wyrażeń.

[Wyrażenia następnej interpretacji](expression-trees-interpreting.md)
