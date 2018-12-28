---
title: Dopasowanie wzorca
description: Dowiedz się, jak wzorce są stosowane w F# do porównywania danych ze struktury logicznej, rozkładania danych do części składowych lub wyodrębnienia informacji z danych.
ms.date: 05/16/2016
ms.openlocfilehash: bb6b41f6d15612e4a65abd4a3d5d7291d84a8f3c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613586"
---
# <a name="pattern-matching"></a>Dopasowanie wzorca

Wzorce są regułami dotyczącymi przekształcania danych wejściowych. Są one używane w całym F# język do porównywania danych ze strukturą logiczną lub strukturami, rozkładania danych do części składowych lub wyodrębnienia informacji z danych na różne sposoby.

## <a name="remarks"></a>Uwagi

Wzorce są stosowane w wielu konstrukcjach języka, takich jak `match` wyrażenia. Są one używane podczas przetwarzania argumentów funkcji w `let` powiązania, wyrażeń lambda i procedurach obsługi wyjątków, skojarzone z `try...with` wyrażenia. Aby uzyskać więcej informacji, zobacz [wyrażenia dopasowań](match-expressions.md), [let — powiązania](functions/let-bindings.md), [wyrażenia Lambda: `fun` — Słowo kluczowe](functions/lambda-expressions-the-fun-keyword.md), i [wyjątków: `try...with` Wyrażenie](exception-handling/the-try-with-expression.md).

Na przykład w `match` wyrażenie *wzorzec* następuje symbol potoku.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Każdy deseń działa jako reguła przekształcania danych wejściowych w jakiś sposób. W `match` wyrażenia, każdy wzorzec jest badany kolejno, można sprawdzić, czy dane wejściowe jest zgodny ze wzorcem. Jeśli zostanie znalezione dopasowanie, wynik wyrażenia jest wykonywana. Jeśli nie zostanie znalezione dopasowanie, bada się następną regułę wzorca. Opcjonalne, jeśli *warunek* część została wyjaśniona w [wyrażenia dopasowań](match-expressions.md).

Obsługiwane wzorce przedstawiono w poniższej tabeli. W czasie wykonywania dane wejściowe są testowane w odniesieniu do każdego z następujących wzorów w określonej kolejności w tabeli, a wzory są stosowane cyklicznie, od pierwszych do ostatniego w jakiej występują w kodzie i od lewej do prawej dla wzorca w każdym wierszu.

|Nazwa|Opis|Przykład|
|----|-----------|-------|
|Wzór stałej|Wszelkie wartości numeryczne, znak lub literał ciągu znaków, stała wyliczenia lub zdefiniowany identyfikator literału|`1.0`, `"test"`, `30`, `Color.Red`|
|Wzorzec identyfikatora|Wartość case złożenia dyskryminowanego, etykieta wyjątku lub przypadek aktywnego wzoru|`Some(x)`<br /><br />`Failure(msg)`|
|Wzór zmiennej|*Identyfikator*|`a`|
|`as` Wzorzec|*wzorzec* jako *identyfikator*|`(a, b) as tuple1`|
|Wzorzec lub|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|Wzorzec i|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Wzór wad|*Identyfikator* :: *identyfikator listy*|`h :: t`|
|Wzorzec listy|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Wzorzec tablicy|[&#124; *pattern_1*;...; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Wzorzec ujęty w nawiasy|( *wzorzec* )|`( a )`|
|Wzór krotki|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Rejestruj wzorzec|{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Wzór symboli wieloznacznych|\_|`_`|
|Wzorzec wraz ze wskazaniem typu|*wzorzec* : *typu*|`a : int`|
|Wpisz wzór testu|:? *Typ* [jako *identyfikator* ]|`:? System.DateTime as dt`|
|Wzorzec zerowy|null|`null`|

## <a name="constant-patterns"></a>Wzory stałych

Wzorce stałych są liczbowych, znaków i literały ciągu stałych wyliczenia (z uwzględnioną nazwą typu wyliczenia). A `match` wyrażenie, które ma tylko stałe wzorce można porównać do wyrażenia CASE w innych językach. Dane wejściowe są porównywane z wartością literału a wzór pasuje, jeśli wartości są równe. Typ literału musi być zgodny z typem danych wejściowych.

Poniższy przykład pokazuje użycie wzorów literału i używa również wzór zmiennej oraz wzoru OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Innym przykładem wzorca literału jest wzorzec oparty na wyliczeniu stałych. Należy określić nazwę typu wyliczenia, gdy używasz stałych wyliczenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Wzorce identyfikatorów

Jeśli wzorzec jest ciągiem znaków, który wchodzi w skład prawidłowy identyfikator, forma identyfikatora Określa, jak odbywa się dopasowanie. Jeśli identyfikator ma więcej niż jeden znak i rozpoczyna się od wielkiej litery, kompilator próbuje wykonać dopasowanie do wzorca identyfikatora. Identyfikator dla tego wzoru może być wartością oznakowaną za pomocą atrybutu literał, dyskryminowanego przypadku złożenia, identyfikatora wyjątku lub przypadek aktywnego wzoru. Jeśli pasujący identyfikator nie zostanie znaleziony, dopasowanie nie powiedzie się i Następna reguła wzorca — wzorzec zmiennych są porównywane w danych wejściowych.

Rozróżniane wzorce połączeń mogą być proste o nazwie przypadków lub mogą mieć wartość, lub krotkę zawierającą wiele wartości. W przypadku wartości, należy określić identyfikator dla wartości. W przypadku spójnej kolekcji musisz podać wzorzec spójnej kolekcji za pomocą identyfikatora dla każdego elementu spójnej kolekcji lub identyfikatorem o nazwie pola dla jednego lub więcej nazwanych pól złożenia. Zobacz przykłady kodu w tej sekcji.

`option` Typ jest złożeniem dyskryminowanym, które posiada dwa przypadki, `Some` i `None`. Jeden przypadek (`Some`) ma wartość, ale drugi (`None`) jest tylko nazwanym przypadkiem. W związku z tym `Some` musi mieć zmienną dla wartości skojarzonej z `Some` wielkości liter, ale `None` musi się pojawiać samodzielnie. W poniższym kodzie zmiennej `var1` jest podana wartość uzyskana przez dopasowanie do `Some` przypadek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

W poniższym przykładzie `PersonName` złożenia dyskryminowanego znajdują się różne ciągi i znaki, które reprezentują możliwe formy nazw. Przypadki złożeń dyskryminowanych są `FirstOnly`, `LastOnly`, i `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Dla sum rozłącznych, które mają pola nazwane możesz użyć znaku równości (=) do wyodrębnienia wartość nazwanego pola. Rozważmy na przykład sumę rozłączną z deklaracją jak następująca.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Można użyć nazwanych pól w wyrażeniu dopasowania wzorca w następujący sposób.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Korzystanie z nazwanego pola jest opcjonalne, więc w poprzednim przykładzie, zarówno `Circle(r)` i `Circle(radius = r)` mają ten sam efekt.

Podczas określania wielu pól, użyj średnika (;) jako separatora.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Aktywne wzorce umożliwiają zdefiniowanie bardziej złożonego niestandardowego wzorca dopasowania. Aby uzyskać więcej informacji na temat wzorców, zobacz [wzorców](active-patterns.md).

Przypadek, w którym identyfikator jest wyjątkiem jest używany podczas dopasowywania wzorca w kontekście obsługi wyjątków. Aby uzyskać informacje o dopasowywaniu do wzorca w obsługę wyjątków, zobacz [wyjątków: `try...with` Wyrażenie](exception-handling/the-try-with-expression.md).

## <a name="variable-patterns"></a>Wzory zmiennej

Wzór zmiennej przypisuje wartość dopasowaną do nazwy zmiennej, która jest dostępna do użytku w wyrażeniu wykonywania znajdującym się po prawej stronie `->` symboli. Sam wzorzec zmiennej nie pasuje do żadnych danych, ale wzorce zmiennej często pojawiają się w innych wzorcach, zatem bardziej złożonych struktur, takich jak tablice, aby być rozłożone na zmienne i kolekcje.

Poniższy przykład ukazuje wzór zmiennej w ramach wzorca krotki.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>jako wzorzec

`as` Wzorzec jest wzorem, który ma `as` dołączoną klauzulę. `as` Klauzuli wiąże pasującą wartość nazwy, które mogą być używane w wyrażeniu wykonywania wyrażenia `match` wyrażenie, lub, w przypadku, gdy ten wzór jest używany w `let` powiązania, nazwa jest dodawana jako wiązanie do zakresu lokalnego.

W poniższym przykładzie użyto `as` wzorca.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>Wzorzec lub

Wzór OR jest używany, gdy dane wejściowe można dopasować do wielu wzorców, a chcesz wykonać w wyniku tego samego kodu. Typy obu stron wzorca OR muszą być zgodne.

Poniższy przykład demonstruje wzorzec OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>Wzorzec i

Wzór AND wymaga, że dane wejściowe są zgodne dwa wzorce. Typy obu stron wzorca AND muszą być zgodne.

Poniższy przykład jest jaki jak `detectZeroTuple` objętego [wzór krotki](https://msdn.microsoft.com/library/#tuple) sekcję w dalszej części tego tematu, ale tutaj zarówno `var1` i `var2` są uzyskiwane jako wartości za pomocą wzorca.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Wzór wad

Wzór minusów służy do rozkładania listy na pierwszy element *head*i listę, która zawiera wszystkie pozostałe elementy *tail*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Wzorzec listy

Wzór listy umożliwia rozkładanie do liczby elementów list. Sam wzorzec listy może odnosić się tylko do list o określonej liczbie elementów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Wzorzec tablicy

Wzór tablicy przypomina wzór listy i może służyć do rozkładania tablic o określonej długości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Wzorzec ujęty w nawiasy

Nawiasy mogą być grupowane wokół wzorców, aby osiągnąć pożądaną łączność. W poniższym przykładzie nawiasy są używane do kontrolowania łączność między wzorcem and wzorcem cons.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Wzór krotki

Wzorzec krotki pasuje do danych wejściowych w formularzu krotki i umożliwia spójnej kolekcji być rozłożone na elementy składowe za pomocą zmiennych dla każdej pozycji w krotce pasujących do wzorca.

Poniższy przykład pokazuje wzór krotki i używa również wzorów literału, wzorów zmiennej oraz wzoru symboli wieloznacznych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Rejestruj wzorzec

Wzór rejestrowania jest używany do rozkładania rekordów w celu wyodrębnienia wartości pól. Wzorzec nie będzie musiał odwoływać się do wszystkich pól rekordu; wszelkie pominięte pola po prostu nie biorą udziału w dopasowywania i nie zostały wyodrębnione.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Wzór symboli wieloznacznych

Wzór symboli wieloznacznych jest reprezentowany przez znak podkreślenia (`_`) znak i pasuje do żadnych danych, podobnie jak wzór zmiennej, z tą różnicą, że dane wejściowe są odrzucane zamiast bycia przypisywanymi do zmiennej. Wzór symboli wieloznacznych jest często używana w ramach innych wzorów jako symbol zastępczy dla wartości, które nie są potrzebne w wyrażeniu na prawo od `->` symboli. Wzór symboli wieloznacznych jest też często używany na końcu listy wzorców do dopasowywania niedopasowanych danych wejściowych. Wzór symboli wieloznacznych jest demonstrowany w wielu przykładach kodu w tym temacie. Zobacz kod poprzedzający dla jednego przykładu.

## <a name="patterns-that-have-type-annotations"></a>Wzorce mające wskazania typów

Wzorce mogą mieć wskazania typów. Te zachowują się jak inne adnotacje i prowadzą wnioskowanie jak inne adnotacje. Nawiasy są wymagane wokół wskazań typów we wzorcach. Poniższy kod przedstawia wzór, który ma adnotacji typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Wpisz wzór testu

Wpisz wzór testu jest używany do dopasowywania danych wejściowych do typu. Typ danych wejściowych jest, aby dopasowanie zakończyło się (lub typem pochodnym) typu określonego we wzorcu, dopasowanie zakończy się pomyślnie.

Poniższy przykład demonstruje typ wzorca testowego.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Wzorzec zerowy

Deseń zerowy pasuje do wartości zerowej, która może pojawić się podczas pracy z typami, które zezwalają na wartości null. Wzorce zerowe są często używane podczas współpracy z kodu .NET Framework. Na przykład, wartość zwracana przez interfejs API programu .NET może być dane wejściowe `match` wyrażenia. Możesz sterować przepływem programu na podstawie, czy wartość zwracana wynosi null, a także na podstawie innych cech zwróconej wartości. Deseń zerowy można użyć, aby zapobiec propagowanie do pozostałej części programu wartości null.

Poniższy przykład używa wzoru null i zmiennych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Zobacz także

- [Wyrażenia dopasowania](match-expressions.md)
- [Wzorce aktywne](active-patterns.md)
- [Dokumentacja języka F#](index.md)