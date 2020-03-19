---
title: Parametry i argumenty
description: Dowiedz się więcej o obsłudze języka języka F# do definiowania parametrów i przekazywania argumentów do funkcji, metod i właściwości.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400198"
---
# <a name="parameters-and-arguments"></a>Parametry i argumenty

W tym temacie opisano obsługę języka do definiowania parametrów i przekazywania argumentów do funkcji, metod i właściwości. Zawiera informacje o tym, jak przekazać przez odwołanie i jak zdefiniować i używać metod, które mogą przyjmować zmienną liczbę argumentów.

## <a name="parameters-and-arguments"></a>Parametry i argumenty

Termin *parametr* jest używany do opisania nazw wartości, które mają być dostarczone. *Argument* terminu jest używany dla wartości podanych dla każdego parametru.

Parametry mogą być określone w krotki lub curried formie lub w jakiejś kombinacji tych dwóch. Argumenty można przekazać przy użyciu jawnej nazwy parametru. Parametry metod można określić jako opcjonalne i podane wartość domyślną.

## <a name="parameter-patterns"></a>Wzorce parametrów

Parametry dostarczane do funkcji i metod są ogólnie wzorami oddzielonymi spacjami. Oznacza to, że w zasadzie każdy z wzorców opisanych w [Dopasuj wyrażenia](match-expressions.md) może być używany na liście parametrów dla funkcji lub elementu członkowskiego.

Metody zwykle używają krotki formularza przekazywania argumentów. Osiąga to jaśniejszy wynik z punktu widzenia innych języków platformy .NET, ponieważ formularz krotki odpowiada sposób, w jaki argumenty są przekazywane w metodach .NET.

Curried formularz jest najczęściej używany z `let` funkcjami utworzonymi przy użyciu powiązań.

Poniższy pseudokod przedstawia przykłady argumentów krotki i curried.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Połączone formularze są możliwe, gdy niektóre argumenty są w krotek, a niektóre nie są.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Inne wzorce mogą być również używane na listach parametrów, ale jeśli wzorzec parametrów nie pasuje do wszystkich możliwych danych wejściowych, może istnieć niekompletne dopasowanie w czasie wykonywania. Wyjątek `MatchFailureException` jest generowany, gdy wartość argumentu nie jest zgodna z wzorcami określonymi na liście parametrów. Kompilator generuje ostrzeżenie, gdy wzorzec parametrów pozwala na niekompletne dopasowania. Co najmniej jeden inny wzorzec jest często przydatne dla list parametrów i to jest wzorzec symboli wieloznacznych. Wzorzec symboli wieloznacznych jest używany na liście parametrów, jeśli chcesz po prostu zignorować wszystkie argumenty, które są dostarczane. Poniższy kod ilustruje użycie wzorca symboli wieloznacznych na liście argumentów.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Wzorzec symboli wieloznacznych może być przydatne, gdy nie są potrzebne argumenty przekazywane w, takich jak w głównym punkcie wejścia do programu, gdy nie są zainteresowani argumentów wiersza polecenia, które są zwykle dostarczane jako tablicy ciąg, jak w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Inne wzorce, które są czasami `as` używane w argumentach są wzorzec i wzorce identyfikatorów skojarzone z dyskryminowanych związków i wzorców aktywnych. Wzorzec unii dyskryminowanej pojedynczego przypadku można użyć w następujący sposób.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Dane wyjściowe są następujące:

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Aktywne wzorce mogą być przydatne jako parametry, na przykład podczas przekształcania argumentu w żądany format, jak w poniższym przykładzie:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

`as` Wzorzec służy do przechowywania dopasowanej wartości jako wartości lokalnej, jak pokazano w poniższym wierszu kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Innym wzorcem, który jest używany od czasu do czasu jest funkcja, która pozostawia ostatni argument bez nazwy, zapewniając, jako treść funkcji, wyrażenie lambda, które natychmiast wykonuje dopasowanie wzorca na argument niejawny. Przykładem tego jest następujący wiersz kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Ten kod definiuje funkcję, która przyjmuje `true` listę rodzajową i `false` zwraca, jeśli lista jest pusta i w przeciwnym razie. Korzystanie z takich technik może utrudnić odczytanie kodu.

Od czasu do czasu wzorce, które obejmują niekompletne dopasowania są przydatne, na przykład, jeśli wiadomo, że listy w programie mają tylko trzy elementy, można użyć wzorca, takiego jak następujące na liście parametrów.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Użycie wzorców, które mają niekompletne dopasowania, najlepiej jest zarezerwowane do szybkiego tworzenia prototypów i innych zastosowań tymczasowych. Kompilator wyda ostrzeżenie dla takiego kodu. Takie wzorce nie mogą obejmować ogólnego przypadku wszystkich możliwych wejść i dlatego nie są odpowiednie dla składników interfejsów API.

## <a name="named-arguments"></a>Nazwane argumenty

Argumenty dla metod można określić przez położenie na liście argumentów oddzielonych przecinkami lub mogą być przekazywane do metody jawnie, podając nazwę, po której następuje znak równości i wartość, która ma zostać przekazana. Jeśli określono przez podanie nazwy, mogą one pojawić się w innej kolejności niż używane w deklaracji.

Nazwane argumenty mogą uczynić kod bardziej czytelnym i bardziej elastycznym do niektórych typów zmian w interfejsie API, takich jak zmiana kolejności parametrów metody.

Nazwane argumenty są dozwolone tylko `let`dla metod, a nie dla funkcji powiązanych, wartości funkcji lub wyrażeń lambda.

Poniższy przykład kodu pokazuje użycie nazwanych argumentów.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

W wywołaniu konstruktora klas można ustawić wartości właściwości klasy przy użyciu składni podobnej do składni nazwanych argumentów. Poniższy przykład pokazuje tę składnię.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Aby uzyskać więcej informacji, zobacz [Konstruktory (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Parametry opcjonalne

Można określić opcjonalny parametr dla metody za pomocą znaku zapytania przed nazwą parametru. Parametry opcjonalne są interpretowane jako typ opcji F#, dzięki czemu można je wysyłać `match` w `Some` zwykły `None`sposób, w jaki są wyszukiwane typy opcji, za pomocą wyrażenia z i . . Parametry opcjonalne są dozwolone tylko dla elementów `let` członkowskich, a nie na funkcje utworzone przy użyciu powiązań.

Istniejące wartości opcjonalne można przekazać do metody `?arg=None` `?arg=Some(3)` według `?arg=arg`nazwy parametru, takiej jak lub lub . Może to być przydatne podczas tworzenia metody, która przekazuje opcjonalne argumenty do innej metody.

Można również użyć `defaultArg`funkcji , która ustawia domyślną wartość opcjonalnego argumentu. Funkcja `defaultArg` przyjmuje parametr opcjonalny jako pierwszy argument, a wartość domyślną jako drugą.

Poniższy przykład ilustruje użycie parametrów opcjonalnych.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Dane wyjściowe są następujące:

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

Na potrzeby c# i Visual Basic interop można `[<Optional; DefaultParameterValue<(...)>]` użyć atrybutów w F#, dzięki czemu wywołania zobaczą argument jako opcjonalne. Jest to równoważne zdefiniowaniu argumentu jako `MyMethod(int i = 3)`opcjonalnego w języku C# jak w .

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Można również określić nowy obiekt jako domyślną wartość parametru. Na przykład `Foo` element członkowski `CancellationToken` może mieć opcjonalne jako dane wejściowe zamiast:

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

Wartość podana jako `DefaultParameterValue` argument musi być zgodna z typem parametru. Na przykład następujące elementy nie są dozwolone:

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

W takim przypadku kompilator generuje ostrzeżenie i całkowicie zignoruje oba atrybuty. Należy zauważyć, `null` że wartość domyślna musi być oznaczona jako typ, ponieważ w przeciwnym `[<Optional; DefaultParameterValue(null:obj)>] o:obj`razie kompilator wywnioskować niewłaściwy typ, tj.

## <a name="passing-by-reference"></a>Przekazywanie przez odwołanie

Przekazywanie wartości F# przez odwołanie obejmuje [byrefs](byrefs.md), które są typami wskaźników zarządzanych. Wskazówki dotyczące tego, jakiego typu należy użyć, są następujące:

- Użyj, `inref<'T>` jeśli wystarczy tylko odczytać wskaźnik.
- Użyj, `outref<'T>` jeśli wystarczy tylko zapisać na wskaźniku.
- Użyj, `byref<'T>` jeśli chcesz zarówno odczytać i zapisać na wskaźniku.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

Ponieważ parametr jest wskaźnikiem, a wartość jest modyfikowalna, wszelkie zmiany wartości są zachowywane po wykonaniu funkcji.

Krotki można użyć jako wartości zwracanej `out` do przechowywania dowolnych parametrów w metodach biblioteki .NET. Alternatywnie można traktować `out` parametr jako `byref` parametr. Poniższy przykład kodu ilustruje obie strony.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parameter — Tablice

Od czasu do czasu konieczne jest zdefiniowanie funkcji, która przyjmuje dowolną liczbę parametrów typu heterogenicznego. Nie byłoby praktyczne, aby utworzyć wszystkie możliwe przeciążone metody, aby uwzględnić wszystkie typy, które mogą być używane. Implementacje platformy .NET zapewniają obsługę takich metod za pośrednictwem funkcji tablicy parametrów. Metoda, która przyjmuje tablicę parametrów w podpisie, może być dostarczona z dowolną liczbą parametrów. Parametry są umieszczane w tablicy. Typ elementów tablicy określa typy parametrów, które mogą być przekazywane do funkcji. Jeśli zdefiniujesz `System.Object` tablicę parametrów jako typ elementu, kod klienta może przekazać wartości dowolnego typu.

W języku F#tablice parametrów można zdefiniować tylko w metodach. Nie można ich używać w autonomicznych funkcjach lub funkcjach zdefiniowanych w modułach.

Tablicę parametrów można `ParamArray` zdefiniować przy użyciu atrybutu. Atrybut `ParamArray` można zastosować tylko do ostatniego parametru.

Poniższy kod ilustruje zarówno wywołanie metody .NET, która przyjmuje tablicę parametrów, jak i definicję typu w języku F#, który ma metodę, która przyjmuje tablicę parametrów.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Po uruchomieniu w projekcie dane wyjściowe poprzedniego kodu są następujące:

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Zobacz też

- [Elementy członkowskie](./members/index.md)
