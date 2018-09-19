---
title: Parametry i argumenty (F#)
description: 'Więcej informacji na temat Obsługa języka F # do definiowania parametrów i przekazanie argumentów do funkcji, metody i właściwości.'
ms.date: 05/16/2016
ms.openlocfilehash: a1e2a70ca560bbb09d2cd10f47485cbe5c5e029d
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288186"
---
# <a name="parameters-and-arguments"></a>Parametry i argumenty

W tym temacie opisano obsługę języka, aby Definiowanie parametrów i przekazanie argumentów do funkcji, metody i właściwości. Zawiera informacje dotyczące sposobu przekazywania według odwołania i jak definiowanie i korzystanie z metod, które może potrwać zmienną liczbę argumentów.

## <a name="parameters-and-arguments"></a>Parametry i argumenty

Termin *parametru* służy do opisywania nazw dla wartości, które powinny być dostarczane. Termin *argument* jest używany dla wartości podanych dla każdego parametru.

Parametry można określić w spójnej kolekcji lub rozwinięte formularza lub kombinację dwóch. Argument jest przekazywany przy użyciu nazwy parametru jawnego. Parametry metod można określone jako opcjonalne i podanej wartości domyślnej.

## <a name="parameter-patterns"></a>Parametr wzorców

Ogólnie rzecz biorąc, parametrów przekazana do funkcji i metod są wzorce rozdzielone spacjami. Oznacza to, że w zasadzie dowolnego wzorce szczegółowo [wyrażenia dopasowań](match-expressions.md) może służyć w liście parametrów dla funkcji lub elementu członkowskiego.

Metody zazwyczaj formularz krotki przekazywanie argumentów. Uzyskuje lepszy wynik z perspektywy innych językach .NET, ponieważ w formularzu krotki pasuje do sposobu argumenty są przekazywane do metody .NET.

Rozwinięte formularza jest najczęściej używana przy użyciu funkcji utworzonych za pomocą `let` powiązania.

Poniższym pseudokodzie pokazano przykłady argumenty rozwinięte i spójnej kolekcji.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Połączone formularze są możliwe w przypadku, gdy niektóre argumenty są w spójnych kolekcjach, a niektóre nie są.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Inne wzorce można również listami parametrów, ale jeśli wzorzec parametr nie jest zgodna wszystkich możliwych danych wejściowych, przyczyną może być niekompletna dopasowania w czasie wykonywania. Wyjątek `MatchFailureException` jest generowany, gdy wartość argumentu jest niezgodna z wzorców określonych na liście parametrów. Kompilator generuje ostrzeżenie, gdy wzorzec parametr umożliwia niekompletne dopasowania. Co najmniej jedno inne wzorzec jest często przydatne w przypadku list parametrów, a to wzór symboli wieloznacznych. Używasz wzór symboli wieloznacznych na liście parametrów, gdy chcesz po prostu ignoruje wszelkie argumenty, które są dostarczane. Poniższy kod ilustruje sposób używania wzorca symbol wieloznaczny, na liście argumentów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Wzór symboli wieloznacznych może być przydatne w każdym przypadku, gdy nie ma potrzeby przekazanych argumentów, na przykład główny punkt wejścia do programu, gdy nie jest konieczne w argumentach wiersza polecenia, które zwykle są dostarczane jako tablicę ciągów, tak jak w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Inne wzorce, które są czasami używane w argumentach są `as` wzorzec i wzorce identyfikatorów skojarzonych z sumy rozłączne i wzorców. Można użyć wzorca złożenia dyskryminowanego pojedynczym przypadku w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Dane wyjściowe są następujące:

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Wzorce aktywne może być przydatne jako parametry, na przykład, podczas transformowania argument na żądany format, jak w poniższym przykładzie:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Możesz użyć `as` wzorzec do przechowywania pasującą wartość jako wartość lokalnego pokazany w następującym wierszu kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Inny wzorzec, który jest czasami używana jest funkcja, która pozostawia ostatni argument nienazwane, zapewniając jako treści funkcji, wyrażenie lambda, która natychmiast wykonuje dopasowanie wzorca niejawnego argumentu. Przykładem jest poniższy wiersz kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Ten kod definiuje funkcję, która przyjmuje listę ogólnych i zwraca `true` Jeśli lista jest pusta, i `false` inaczej. Korzystanie z takich technik może uczynić kod czytelność.

Od czasu do czasu wzorców, które obejmują niekompletne dopasowania są przydatne, na przykład, jeśli wiesz, że tylko trzy elementy listy w programie, mogą korzystania z wzorca podobnie do następującej listy parametrów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Użycie wzorce mające niekompletne dopasowania najlepiej jest zarezerwowana do szybkiego tworzenia prototypów i inne zastosowania tymczasowego. Kompilator zgłosi ostrzeżenie dla tego kodu. Takie wzorce nie obejmują generalnie w przypadku wszystkich możliwych danych wejściowych i dlatego nie są odpowiednie dla składnika API.

## <a name="named-arguments"></a>Argumenty nazwane

Argumenty dla metod, można określić za pomocą pozycji na liście argumentów rozdzielonych przecinkami lub one mogą być przekazywane do metody jawnie, podając nazwę, w którym następuje znak równości i wartości, które mają być przekazane w. Jeśli zostanie określony, podając nazwę, może znajdować się w innej kolejności z używanym w deklaracji.

Argumenty nazwane może uczynić kod bardziej czytelne i bardziej potężnej niektórych typów zmian w interfejsie API, takie jak zmiany kolejności parametrów metody.

Argumenty nazwane są dozwolone tylko w przypadku metod, nie dla `let`-powiązane funkcje, wartości funkcji lub wyrażenia lambda.

Poniższy przykład kodu demonstruje użycie argumentów nazwanych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

W wywołaniu konstruktora klasy można ustawić wartości właściwości klasy przy użyciu składni podobnej do nazwanych argumentów. Poniższy przykład pokazuje tej składni.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Aby uzyskać więcej informacji, zobacz [Konstruktorzy (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Parametry opcjonalne

Można określić opcjonalny parametr dla metody, przy użyciu znaku zapytania przed nazwą parametru. Następujące parametry opcjonalne są interpretowane jako typów opcji języka F #, dzięki czemu można tworzyć zapytania je w zwykły sposób, że zapytania są typy opcji za pomocą `match` wyrażenie `Some` i `None`. Następujące parametry opcjonalne są dozwolone tylko w elementach członkowskich, nie na funkcje nie powstały przy użyciu `let` powiązania.

Można również użyć funkcji `defaultArg`, który ustawia domyślną wartość opcjonalny argument. `defaultArg` Funkcja przyjmuje opcjonalny parametr jako pierwszy argument i wartość domyślną, jako drugiego.

Poniższy przykład ilustruje użycie parametrów opcjonalnych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Dane wyjściowe są następujące:

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Przekazywanie poprzez odwołanie

Przekazywanie F # wartości według odwołania polega na [zkratka](byrefs.md), które są typami wskaźnika zarządzanych. Wskazówki dla jakiego typu użycia jest następująca:

* Użyj `inref<'T>` Jeśli wymagane jest tylko do odczytu wskaźnika.
* Użyj `outref<'T>` Jeśli wymagane jest tylko do zapisu do wskaźnika.
* Użyj `byref<'T>` Chcąc odczytywać i zapisywać wskaźnika.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

Ponieważ tego parametru jest wskaźnik, a wartość jest modyfikowalna, wszelkie zmiany wartości są zachowywane po wykonaniu funkcji.

Spójna kolekcja można użyć jako wartości zwracanej, do przechowywania wszelkich `out` parametry metody biblioteki .NET. Alternatywnie możesz traktować `out` jako parametr `byref` parametru. Poniższy przykład kodu ilustruje obu kierunkach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parameter — Tablice

Czasami jest konieczne jest określenie funkcji, która przyjmuje dowolną liczbę parametrów typu heterogenicznych. Nie jest praktyczne utworzyć wszystkie możliwe metody przeciążone do konta dla wszystkich typów, które mogłyby zostać użyte. Implementacje platformy .NET zapewnia obsługę takich metod za pomocą funkcji tablicy parametrów. Z dowolnej liczby parametrów można podać metodę, która przyjmuje jeho signatura tablicy parametrów. Parametry są umieszczane w tablicy. Określa typ elementów tablicy, typy parametrów, które mogą być przekazywane do funkcji. Jeśli zdefiniujesz tablicy parametrów za pomocą `System.Object` jako typ elementu następnie kod klienta można przekazać wartości dowolnego typu.

W języku F # tablice parametrów mogą można zdefiniować tylko w metodach. Nie można ich używać w autonomicznej lub funkcji, które są definiowane w modułach.

Tablica parametrów są definiowane za pomocą `ParamArray` atrybutu. `ParamArray` Atrybut można stosować tylko do ostatniego parametru.

Poniższy kod ilustruje obie wywołanie metody .NET, która przyjmuje tablicy parametrów i definicji typu w F #, który ma metodę, która przyjmuje tablicy parametrów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Po uruchomieniu w projekcie, dane wyjściowe poprzedniego kodu jest następująca:

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](members/index.md)
