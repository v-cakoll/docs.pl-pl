---
title: Ciągi (F#)
description: 'Dowiedz się, jak typu "string" F # reprezentuje niezmienny tekst jako sekwencja znaków Unicode.'
ms.date: 05/16/2016
ms.openlocfilehash: 21971602093bc84b0df47d4ae46a14fb936c28bb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799346"
---
# <a name="strings"></a>Ciągi

> [!NOTE]
Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

`string` Typu reprezentuje niezmienny tekst jako sekwencja znaków Unicode. `string` jest aliasem dla `System.String` w .NET Framework.

## <a name="remarks"></a>Uwagi

Literały ciągów są rozdzielone znakiem cudzysłowu ("). Znak ukośnika odwrotnego ( \\ ) jest używany do kodowania niektórych znaków specjalnych. Ukośnik odwrotny i następny znak razem są określane jako *sekwencji unikowej*. Znak ucieczki sekwencje obsługiwane w F # ciąg, który literały są wyświetlane w poniższej tabeli.

|Znak|Sekwencja unikowa|
|---------|---------------|
|Backspace|`\b`|
|nowy wiersz|`\n`|
|Powrót karetki|`\r`|
|Tab|`\t`|
|Ukośnik odwrotny|`\\`|
|Znak cudzysłowu|`\"`|
|Apostrof|`\'`|
|znak Unicode|`\uXXXX` lub `\UXXXX` (gdzie `X` wskazuje cyfra szesnastkowa)|

Jeśli poprzedzone symbolem @ literał jest ciąg verbatim. Oznacza to, że wszelkie sekwencje ucieczki są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.

Ponadto ciąg mogą być ujęte w cudzysłowy Potrójna. W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu. Aby określić ciąg, który zawiera osadzony jako ciąg, możesz użyć ciąg verbatim lub ciąg potrójnych cudzysłowach. Jeśli używasz ciąg verbatim, należy określić dwa znaki cudzysłowu do wskazania znak pojedynczego cudzysłowu. Użycie ciągu potrójnych cudzysłowach, można użyć znaków pojedynczego cudzysłowu, bez nich przeanalizowany jako końca ciągu. Ta technika może być przydatne podczas pracy z XML lub innych struktur, które zawierają osadzone znaki cudzysłowu.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

W kodzie ciągów zawierających podziały wierszy są akceptowane i podziałów wiersza są interpretowane dosłownie jako tabulacji, chyba że znak ukośnika odwrotnego jest ostatni znak przed podziału wiersza. Spacja wiodąca w następnym wierszu jest ignorowana, gdy jest używany znak ukośnika odwrotnego. Poniższy kod tworzy ciąg `str1` wartością `"abc\ndef"` i ciąg `str2` wartością `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Można uzyskać dostęp do poszczególnych znaków w ciągu za pomocą składni tablicy w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Dane wyjściowe są `b`.

Lub wyodrębnić podciągi przy użyciu składni wycinek tablicy, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Dane wyjściowe są następujące:

```
abc
def
```

Ciągi ASCII mogą być reprezentowane przez tablice bajtów bez znaku, wpisz `byte[]`. Dodaj sufiks `B` z ciągiem literału, aby wskazać, że ciąg ASCII. Literały ciągów znaków ASCII używany z tablic bajtowych obsługują ten sam sekwencje ucieczki jako ciągi znaków Unicode, z wyjątkiem sekwencje unikowe Unicode.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operatory ciągów

Istnieją dwa sposoby łączenia ciągów: za pomocą `+` operatora lub za pomocą `^` operatora. `+` Operator zachowuje zgodność z obsługi funkcji ciągów .NET Framework.

Poniższy przykład ilustruje ciągów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Klasa String

Ponieważ typ ciągu w języku F # jest faktycznie .NET Framework `System.String` wpisz wszystkie `System.String` składowe są dostępne. Obejmuje to `+` operatora, który jest używany do łączenia ciągów, `Length` właściwości i `Chars` właściwość, która zwraca ciąg w postaci tablicy znaków Unicode. Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.

Za pomocą `Chars` właściwość `System.String`, dostęp do poszczególnych znaków w ciągu, określając indeksu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Parametry modułu

Dodatkowe funkcje obsługi ciągu znajduje się w `String` modułu w `FSharp.Core` przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Core.String — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
