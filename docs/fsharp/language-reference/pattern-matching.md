---
title: Dopasowanie wzorca (F#)
description: "Dowiedz się, jak wzorce są używane w języku F # do porównywania danych o strukturze logicznej Rozłóż danych na elementów składowych i wyodrębnienia informacji z danych."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5562ee98-e2f1-4dcd-8e2f-16ae27baaade
ms.openlocfilehash: 7c7a3110a8f34c0c96c12d4584010a9ac4b485fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pattern-matching"></a>Dopasowanie wzorca

Wzorce są reguły przekształcania danych wejściowych. Są one używane w całej języka F # do porównywania danych za pomocą struktury logicznej lub struktury, Rozłóż danych na elementów składowych lub wyodrębnienia informacji z danych na różne sposoby.


## <a name="remarks"></a>Uwagi
Wzorce są używane w wielu konstrukcji języka, takich jak `match` wyrażenia. Są one używane podczas przetwarzania argumentów funkcji w `let` powiązań, wyrażenia lambda w programy obsługi wyjątków, skojarzone z `try...with` wyrażenia. Aby uzyskać więcej informacji, zobacz [wyrażenia dopasowania](match-expressions.md), [let — powiązania](functions/let-bindings.md), [wyrażenia Lambda: `fun` — słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md), i [wyjątkami: `try...with` Wyrażenie](exception-handling/the-try-with-expression.md).

Na przykład w `match` wyrażenie *wzorzec* jest poniżej symbol potoku.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Każdy wzorzec działa jako regułę do przekształcania danych wejściowych w inny sposób. W `match` wyrażenia, każdy wzorzec jest zbadać z kolei jeśli danych wejściowych jest zgodny z wzorcem. Jeśli dopasowanie zostanie znaleziony, jest wykonywany wynik wyrażenia. Jeśli nie, jest testowany następnego reguł wzorca. Kiedy opcjonalne *warunku* opisanej w części [wyrażenia dopasowania](match-expressions.md).

W poniższej tabeli przedstawiono obsługiwane wzorce. W czasie wykonywania danych wejściowych jest testowana każdego z następujących wzorce w kolejności podanej w tabeli i wzorce są stosowane rekursywnie z najpierw do ostatniego pojawiających się w kodzie i od lewej do prawej wzorców w każdym wierszu.

|Nazwa|Opis|Przykład|
|----|-----------|-------|
|Stałe wzorzec|Wszelkie liczbowe, znak, lub literału ciągu, stała wyliczenia lub identyfikatora literału zdefiniowanego|`1.0`, `"test"`, `30`, `Color.Red`|
|Identyfikator — wzorzec|Wartość działania case rozróżnianą Unię, etykiety wyjątków lub w przypadku — aktywny wzorzec|`Some(x)`<br /><br />`Failure(msg)`|
|Variable — wzorzec|*Identyfikator*|`a`|
|`as`wzorzec|*wzorzec* jako *identyfikator*|`(a, b) as tuple1`|
|LUB wzorca|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|I wzorzec|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Cons — wzorzec|*Identyfikator* :: *identyfikator listy*|`h :: t`|
|List — wzorzec|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Array — wzorzec|[&#124; *pattern_1*;...; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Parenthesized — wzorzec|( *wzorzec* )|`( a )`|
|Tuple — wzorzec|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Record — wzorzec|{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Wildcard — wzorzec|_|`_`|
|Wzorzec wraz z adnotacji typu|*wzorzec* : *typu*|`a : int`|
|Typ test — wzorzec|:? *Typ* [jako *identyfikator* ]|`:? System.DateTime as dt`|
|Null — wzorzec|null|`null`|

## <a name="constant-patterns"></a>Wzorce stałej
Wzorce stałej są stałe wyliczenie alfanumeryczne, znak i literałów ciągu (z nazwą typu wyliczenia uwzględnione). A `match` wyrażenie, które tylko stałe wzorce można porównać do instrukcji case w innych językach. Dane wejściowe jest porównywana z wartością literału i wzorzec jest zgodny, jeśli wartości są równe. Typ literału musi być zgodny z typem danych wejściowych.

Poniższy przykład przedstawia użycie literału wzorców i używa również zmiennej wzoru i lub.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Innym przykładem deseniu literału to wzorzec oparty na stałe wyliczenia. Należy określić nazwę typu wyliczenia używania stałe wyliczenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Identyfikator wzorce
Jeśli wzorzec jest ciąg znaków, który wchodzi w skład prawidłowy identyfikator, formularz identyfikatora Określa, jak jest dopasowywany wzorzec. Jeśli identyfikator jest dłuższy niż jeden znak i rozpoczyna się wielką literę, kompilator próbuje dopasować je do wzorca identyfikatora. Identyfikator dla tego wzorca może być wartością atrybutu literałowego, przypadek Unii rozłącznej, identyfikator wyjątku lub case — aktywny wzorzec. Przypadku nieznalezienia nie dopasowania identyfikatora, dopasowania nie powiedzie się i następnego reguł wzorca wzorcu zmiennej jest porównywany z danych wejściowych.

Wzorce Unii rozłącznych może być prosty o nazwie przypadków albo mogą mieć wartości lub spójnych kolekcji zawierający wiele wartości. Jeśli istnieje wartość, należy określić identyfikator dla wartości. W przypadku spójnej kolekcji należy podać wzorzec krotki z identyfikatora dla każdego elementu spójnej kolekcji lub identyfikatora nazwą pola dla jednego lub więcej o nazwie pól union. Przykłady kodu w tej sekcji przykłady.

`option` Typu jest rozróżnianą Unię z dwóch przypadków `Some` i `None`. Jeden przypadek (`Some`) ma wartość, ale druga (`None`) jest nazwane przypadku. W związku z tym `Some` musi mieć zmiennej wartość skojarzoną z `Some` , ale `None` musi występować samodzielnie. W poniższym kodzie zmiennej `var1` znajduje się wartość, która uzyskuje się przez dopasowanie do `Some` case.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

W poniższym przykładzie `PersonName` rozróżnianą Unię zawiera kombinację ciągów znaków, które reprezentują możliwe formy nazwy. Przypadków Unii rozłącznych są `FirstOnly`, `LastOnly`, i `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Dla rozłączne, które mają nazwane pola należy używać znak równości (=), aby wyodrębnić wartość pola o nazwie. Rozważmy na przykład rozróżnianą Unię z deklaracją podobne do następujących.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Można użyć nazwanego pola w wyrażeniu dopasowania wzorca w następujący sposób.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Korzystanie z nazwane pole jest opcjonalne, więc w poprzednim przykładzie zarówno `Circle(r)` i `Circle(radius = r)` mają ten sam efekt.

Podczas określania wielu pól, użyj średnika (;) jako separatora.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Wzorce aktywne umożliwiają definiowanie bardziej złożonych dopasowanie wzorca niestandardowych. Aby uzyskać więcej informacji na temat aktywne wzorce, zobacz [aktywne wzorce](active-patterns.md).

Przypadek, w którym wyjątek stanowi identyfikator jest używany podczas dopasowywania w kontekście obsługi wyjątków do wzorca. Informacje o wzorzec dopasowany w obsłudze wyjątków, zobacz [wyjątkami: `try...with` wyrażenia](exception-handling/the-try-with-expression.md).


## <a name="variable-patterns"></a>Wzorce zmiennych
Variable — wzorzec przypisuje wartość filtrowanego na nazwę zmiennej, która jest dostępna do użycia w wyrażeniu wykonywania z prawej strony `->` symbolu. Variable — wzorzec wyłącznie pasuje do żadnych danych, ale wzorce zmiennych często pojawiają się w innych wzorcach, dlatego włączenie bardziej złożonych struktur przykład spójnych kolekcji i tablic, aby być rozłożone na zmienne.

W poniższym przykładzie pokazano zmiennej wzorca w wzorzec spójnej kolekcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>AS — wzorzec
`as` Wzorzec jest wzorzec, który ma `as` klauzuli dołączone do niego. `as` Klauzuli wiąże wprowadzona wartość nazwę używaną w wyrażeniu wykonywania `match` wyrażenia, lub, w którym ten wzorzec jest używany w przypadku `let` powiązanie, nazwa zostanie dodany jako powiązanie do zakresu lokalnego.

W poniższym przykładzie użyto `as` wzorca.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>LUB wzorca
Wzorzec lub jest używana, gdy dane wejściowe może dopasować wielu wzorców, i chcesz wykonać ten sam kod w związku z tym. Typy wzorzec lub obu stron muszą być zgodne.

W poniższym przykładzie pokazano lub wzorzec.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>I wzorzec
Wzorzec i musi być zgodna dwa wzorce w danych wejściowych. Typy obie strony wzorca i muszą być zgodne.

Poniższy przykład przypomina `detectZeroTuple` pokazano [Tuple — wzorzec](https://msdn.microsoft.com/library/#tuple) dalszej części tego tematu, ale tutaj zarówno `var1` i `var2` są uzyskiwane jako wartości przy użyciu wzorca i.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Cons — wzorzec
Wzorzec wad służy do Rozłóż listy na pierwszym elementem *head*oraz listę zawierającą wszystkie pozostałe elementy *tail*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>List — wzorzec
List — wzorzec umożliwia listy, aby być rozłożone na liczbę elementów. List — wzorzec sam może dopasować tylko listy określoną liczbę elementów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Array — wzorzec
Array — wzorzec podobny wzorzec listy i może służyć do dekompozycji tablice o określonej długości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Parenthesized — wzorzec
Mogą być grupowane nawiasów wokół wzorców w celu osiągnięcia żądanej łączność. W poniższym przykładzie nawiasy są używane do kontrolowania łączność między wzoru i i wad.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Tuple — wzorzec
Tuple — wzorzec jest zgodny z danych wejściowych w postaci spójnej kolekcji i umożliwia spójnej kolekcji być rozłożone na jego elementy składowe przy użyciu wzorca dopasowania zmienne dla każdej pozycji w spójnej kolekcji.

W poniższym przykładzie pokazano wzorzec spójnej kolekcji i używa również wzorce literału, wzorce zmiennych i wzorcu symboli wieloznacznych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Record — wzorzec
Wzorzec rekord jest używany do dekompozycji rekordów Wyodrębnij wartości pól. Wzorzec nie musi odwoływać się do wszystkich pól rekordu; wszystkie pola pominięcia po prostu nie uczestniczą w odpowiadającym i nie są wyodrębniane.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Wildcard — wzorzec
Wzorzec wieloznaczny jest reprezentowany przez znak podkreślenia (`_`) znaków, a wszystkie dane wejściowe, podobnie jak wzorcu zmiennej jest zgodna z tą różnicą, że dane wejściowe są usuwane zamiast przypisany do zmiennej. Wzorzec wieloznaczny jest często używana w innych wzorcach jako symbol zastępczy wartości, które nie są wymagane w wyrażeniu po prawej stronie `->` symbolu. Wzorzec wieloznaczny jest również często używane na końcu Lista wzorców odpowiadające niedopasowane udziału. Wzorzec wieloznaczny jest przedstawiona w wiele przykładów kodu, w tym temacie. Zobacz poprzedni kod na jednym z przykładów.


## <a name="patterns-that-have-type-annotations"></a>Wzorce, które mają adnotacje typu
Wzorce może mieć adnotacji typu. Te przypominają innych adnotacji typu i przewodnik wnioskowania podobnie jak inne adnotacji typu. Wymagane są nawiasów wokół adnotacji typu w wzorce. Poniższy kod przedstawia wzorzec, który ma adnotację typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Typ Test — wzorzec
Wzorzec testu typu jest używany do dopasowywania przed typem danych wejściowych. Typ danych wejściowych jest dopasowanie do (lub typu pochodnego) typu określonego we wzorcu dopasowania zakończy się pomyślnie.

W poniższym przykładzie pokazano wzorzec testu typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Null — wzorzec
Null — wzorzec zgodna z wartością null może wystąpić podczas pracy z typami zezwalających na wartość null. Wzorce wartości null są często używane podczas współpracy z kodu .NET Framework. Na przykład wartość zwracaną przez interfejs API programu .NET mogą być dane wejściowe `match` wyrażenia. Można sterować przepływem programu na podstawie, czy wartość zwracana jest wartość null, a także na innych właściwości zwracanej wartości. Null — wzorzec umożliwia uniemożliwić propagowanie z resztą programu wartości null.

W poniższym przykładzie użyto wzoru null i zmiennej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Zobacz też
[Wyrażenia dopasowania](match-expressions.md)

[Wzorce aktywne](active-patterns.md)

[Dokumentacja języka F #](index.md)
