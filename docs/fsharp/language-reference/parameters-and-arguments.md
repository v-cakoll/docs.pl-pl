---
title: Parametry i argumenty (F#)
description: "Więcej informacji o obsługę języka F # do definiowania parametrów i przekazywanie argumentów do funkcji, właściwości i metod."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9b37a5c4-9263-4513-822a-fbb0d1004254
ms.openlocfilehash: 50f54bacd9ba7ec20a7151794734f93200df9f2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="parameters-and-arguments"></a>Parametry i argumenty

W tym temacie opisano obsługę języka zdefiniowanie parametrów i przekazywanie argumentów do funkcji, właściwości i metod. Zawiera informacje o sposobie przekazywane przez odwołanie i jak definiowanie i korzystanie z metod, które można wykonać zmienną liczbę argumentów.


## <a name="parameters-and-arguments"></a>Parametry i argumenty
Termin *parametru* jest używany do opisu nazwy dla wartości, które mają być dostarczone. Termin *argument* jest używany dla wartości podane dla każdego parametru.

Parametry można określić w spójnej kolekcji lub rozwinięte formularza lub kombinację obu. Argument jest przekazywany za pomocą nazwy parametru jawnego. Parametry metody można określony jako opcjonalne i określoną wartość domyślną.


## <a name="parameter-patterns"></a>Parametr wzorce
Parametry dostarczone do funkcji i metod są ogólnie rzecz biorąc, wzorce rozdzielone spacjami. Oznacza to, że w zasadzie żadnego wzorce opisem w temacie [wyrażenia dopasowania](match-expressions.md) można użyć listy parametrów dla funkcji lub elementu członkowskiego.

Metody zazwyczaj używają formy krotki przekazywanie argumentów. Osiąga jaśniejszy wyników z punktu widzenia innych języków .NET, ponieważ sposób argumenty są przekazywane w metodach .NET jest zgodna z postaci spójnej kolekcji.

Rozwinięte formularza jest najczęściej używana z funkcji utworzonych za pomocą `let` powiązania.

Następujące pseudocode przedstawiono przykłady argumenty curried i spójnej kolekcji.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Gdy niektóre argumenty są w krotek, a niektóre nie są możliwe są połączone formularzy.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Innymi wzorami można również w listy parametrów, ale jeśli wzorzec parametru jest niezgodny z wszystkich możliwych danych wejściowych, być może niepełne dopasowania w czasie wykonywania. Wyjątek `MatchFailureException` jest generowany, gdy wartość argumentu jest niezgodny z określonych na liście parametrów wzorców. Kompilator generuje ostrzeżenie, gdy umożliwia niepełne dopasowania wzorca parametru. Co najmniej jedno inne wzorzec jest często przydatne w przypadku listy parametrów, a to wzorzec wieloznaczny. Na liście parametrów będą używane wzorcu symboli wieloznacznych, gdy chcesz po prostu zignoruj argumenty, które są dostarczane. Poniższy kod przedstawia użycie wzorzec wieloznaczny w listy argumentów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Wzorzec wieloznaczny może być przydatne, gdy nie ma potrzeby przekazanych argumentów, takich jak główny punkt wejścia do programu, gdy nie jest konieczne w argumentach wiersza polecenia, które zwykle są dostarczane w postaci tablicy ciągów, zgodnie z poniższym kodem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Inne wzorce, które są czasami używane w argumentach są `as` wzorzec oraz skojarzonych z rozłączne i wzorce aktywne wzorce identyfikator. Można użyć wzorcu jeden przypadek Unii rozłącznych w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Dane wyjściowe są następujące:

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Wzorce aktywne może służyć jako parametrów, na przykład gdy przekształcania argumentu w wybranym formacie, jak w poniższym przykładzie:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Można użyć `as` wzorzec do przechowywania wprowadzona wartość jako wartości lokalnej, jak to pokazano w następującym wierszu kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Inny wzorzec, który jest czasami używana jest funkcja, pozostawiając ostatni argument nienazwane zapewniając jako treść funkcji, natychmiast wykonujące dopasowania wzorca na niejawnego argumentu wyrażenia lambda. Na przykład jest następujący wiersz kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Ten kod definiuje funkcję, która przyjmuje listę ogólnych i zwraca `true` Jeśli lista jest pusta, i `false` inaczej. Korzystanie z takich technik wprowadzić kod czytelność.

Czasami wzorców, które obejmują niepełne dopasowania są przydatne, na przykład, jeśli wiadomo, że tylko trzy elementy list w programie, można na przykład wzorzec podobnie do następującej listy parametrów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Korzystanie z wzorców, które mają niepełne dopasowania najlepiej jest zarezerwowana dla szybkie tworzenie prototypów i innych celów tymczasowego. Kompilator wyświetli ostrzeżenie dla takich kodu. Takie wzorce nie obejmuje również ogólne wszystkich możliwych danych wejściowych i w związku z tym nie są odpowiednie dla składnika interfejsów API.

## <a name="named-arguments"></a>Argumenty nazwane
Według położenia w postaci listy rozdzielanej przecinkami argument można określić argumentów dla metody lub ich mogą zostać przekazane do metody jawnie przez podanie nazwy, a po niej znak równości i wartość, należy przesłać. Jeśli zostanie określona, podając nazwę, może się pojawić w innym porządku niż w deklaracji.

Argumenty nazwane można wprowadzić kod bardziej przejrzysta i bardziej dostosowywalne określone typy zmian w interfejsie API, takie jak zmiany kolejności parametrów metody.

Nazwane argumenty nie są dozwolone tylko dla metod, nie dla `let`-powiązanych funkcji, wartości funkcji lub wyrażenia lambda.

Poniższy przykład kodu pokazuje użycie argumentów nazwanych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

W wywołaniu konstruktora klasy można ustawić wartości właściwości klasy przy użyciu składni podobny do nazwanych argumentów. W poniższym przykładzie przedstawiono tej składni.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Aby uzyskać więcej informacji, zobacz [Konstruktorzy (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Parametry opcjonalne
Można określić opcjonalny parametr dla metody przy użyciu znaku zapytania przed nazwą parametru. Parametry opcjonalne są interpretowane jako typ opcji języka F #, aby mogła zbadać je w zwykły sposób, że typy opcji będą pytani przy użyciu `match` wyrażenie z `Some` i `None`. Parametry opcjonalne są dozwolone tylko w elementach członkowskich, nie na funkcji utworzonych za pomocą `let` powiązania.

Można także użyć funkcji `defaultArg`, który ustawia domyślną wartość opcjonalny argument. `defaultArg` Funkcja przyjmuje opcjonalny parametr jako pierwszego argumentu oraz wartość domyślną jako drugiego.

Poniższy przykład przedstawia użycie parametrów opcjonalnych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Dane wyjściowe są następujące:

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Przekazywanie poprzez odwołanie
F # obsługuje `byref` — słowo kluczowe, która określa, że parametr jest przekazywany przez odwołanie. Oznacza to, że wszystkie zmiany na wartość są zachowywane po wykonaniu funkcji. Wartości określone na `byref` parametr musi być modyfikowalną. Alternatywnie można przekazać komórki odwołań odpowiedniego typu.

Przekazywanie poprzez odwołanie w językach .NET ewoluował jako sposób więcej niż jedną wartość zwrócona przez funkcję. W F # można zwrócić krotka w tym celu, lub użyj komórki referencyjnych jako parametr. `byref` Głównie podano parametru do współdziałania z bibliotekami .NET.

Poniższe przykłady przedstawiają użycie `byref` — słowo kluczowe. Należy pamiętać, że gdy komórka odwołania można użyć jako parametru, użytkownik musi utworzyć odwołanie do komórki jako wartość nazwanego i używać go jako parametru nie wystarczy dodać `ref` operatora, jak pokazano w pierwszym wywołaniu `Increment` w poniższym kodzie. Ponieważ tworzenie komórka odwołania tworzy kopię odpowiednia wartość, pierwsze wywołanie po prostu zwiększa wartości tymczasowej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

Krotka jako wartości zwracane służy do przechowywania wszelkich `out` parametrów w metodach biblioteki .NET. Alternatywnie można traktować `out` parametr jako `byref` parametru. W poniższym przykładzie kodu przedstawiono w obu kierunkach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Parameter — Tablice
Czasami jest niezbędne zdefiniować funkcję, która przyjmuje dowolnej liczby parametrów typu heterogenicznych. Nie jest praktyczne utworzyć wszystkie możliwe metody przeciążonej do konta dla wszystkich typów, które mogłyby zostać użyte. Implementacje .NET zapewniają obsługę tych metod, za pomocą funkcji tablicy parametrów. Z dowolnej liczby parametrów można podać metodę, która przyjmuje tablicy parametrów w podpisie. Parametry są umieszczane w tablicy. Typ elementów tablicy Określa typy parametrów, które mogą zostać przekazane do funkcji. W przypadku definiowania tablicy parametrów z `System.Object` jako typ elementu następnie kod klienta można przekazać wartości dowolnego typu.

W języku F # można zdefiniować w metodach tylko tablice parametrów. Nie można ich używać w autonomicznej lub funkcji, które są definiowane w modułach.

Zdefiniuj tablicy parametrów przy użyciu `ParamArray` atrybutu. `ParamArray` Atrybut można stosować tylko do ostatniego parametru.

Poniższy kod ilustruje, zarówno podczas wywoływania metody .NET, która przyjmuje tablicy parametrów, jak i definicja typu w języku F #, który ma metodę, która przyjmuje tablicy parametrów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Gdy są uruchomione w projekcie, dane wyjściowe poprzedniego kodu jest następujący:

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](members/index.md)
