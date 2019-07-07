---
title: Ciągi
description: Dowiedz się, jak F# typu "string" reprezentuje niezmienny tekst jako sekwencja znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: b252aef7d7e6e299df8282407198714971e80cd5
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610164"
---
# <a name="strings"></a>Ciągi

> [!NOTE]
> Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

`string` Typu reprezentuje niezmienny tekst jako sekwencja znaków Unicode. `string` jest aliasem dla `System.String` w .NET Framework.

## <a name="remarks"></a>Uwagi

Literały ciągów są rozdzielone znakiem cudzysłowu ("). Znak ukośnika odwrotnego ( \\ ) jest używany do kodowania niektórych znaków specjalnych. Ukośnik odwrotny i następny znak razem są określane jako *sekwencji unikowej*. Obsługiwane w sekwencjach specjalnych F# literały ciągów są wyświetlane w poniższej tabeli.

|Znak|Sekwencja unikowa|
|---------|---------------|
|Alerty|`\a`|
|Backspace|`\b`|
|Wysuw strony|`\f`|
|nowy wiersz|`\n`|
|Powrót karetki|`\r`|
|Tab|`\t`|
|tabulator pionowy|`\v`|
|Ukośnik odwrotny|`\\`|
|Znak cudzysłowu|`\"`|
|Apostrof|`\'`|
|znak Unicode|`\DDD` (gdzie `D` wskazuje wartości dziesiętnej cyfrę; zakres 000 - 255; np. `\231` = "ç")|
|znak Unicode|`\xHH` (gdzie `H` wskazuje cyfra szesnastkowa; zakres 00 - FF; np. `\xE7` = "ç")|
|znak Unicode|`\uHHHH` (UTF-16) (gdzie `H` wskazuje cyfra szesnastkowa; zakres 0000 – FFFF;  np. `\u00E7` = "ç")|
|znak Unicode|`\U00HHHHHH` (UTF-32) (gdzie `H` wskazuje cyfra szesnastkowa; zakres 000000 - 10FFFF;  np. `\U0001F47D` = "👽")|

> [!IMPORTANT]
> `\DDD` Sekwencja unikowa to Notacja dziesiętna, a nie ósemkowy podobnie jak w innych językach. W związku z tym, cyfr `8` i `9` są prawidłowe oraz sekwencję `\032` reprezentuje spację (U + 0020), byłoby tego samego punktu kodu w notacji ósemkowej `\040`.

> [!NOTE]
> Jest ograniczone do zakresu od 0 - 255 (0xFF) `\DDD` i `\x` sekwencje ucieczki są faktycznymi [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) znak zestawu, ponieważ odpowiadający 256 pierwszych punkty kodowe Unicode.

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

Ponieważ wpisać ciąg F# jest faktycznie .NET Framework `System.String` wpisz wszystkie `System.String` składowe są dostępne. Obejmuje to `+` operatora, który jest używany do łączenia ciągów, `Length` właściwości i `Chars` właściwość, która zwraca ciąg w postaci tablicy znaków Unicode. Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.

Za pomocą `Chars` właściwość `System.String`, dostęp do poszczególnych znaków w ciągu, określając indeksu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Parametry modułu

Dodatkowe funkcje obsługi ciągu znajduje się w `String` modułu w `FSharp.Core` przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Core.String — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
