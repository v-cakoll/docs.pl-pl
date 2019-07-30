---
title: Ciągi
description: Dowiedz się F# , jak typ "String" reprezentuje niezmienny tekst jako sekwencję znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 284de939c90c4d9d4ea064fb4db1fb90a37038e2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627105"
---
# <a name="strings"></a>Ciągi

> [!NOTE]
> Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

`string` Typ reprezentuje niezmienny tekst jako sekwencję znaków Unicode. `string`jest aliasem dla `System.String` .NET Framework.

## <a name="remarks"></a>Uwagi

Literały ciągów są rozdzielane znakami cudzysłowu ("). Znak ukośnika odwrotnego \\ () jest używany do kodowania niektórych znaków specjalnych. Ukośnik odwrotny i następny znak razem są znane jako *sekwencja ucieczki*. Sekwencje ucieczki F# obsługiwane w literałach ciągów są pokazane w poniższej tabeli.

|Znak|Sekwencja ucieczki|
|---------|---------------|
|Alerty|`\a`|
|Backspace|`\b`|
|Kanał informacyjny formularza|`\f`|
|Ani|`\n`|
|Znak powrotu karetki|`\r`|
|Tab|`\t`|
|Tabulator pionowy|`\v`|
|Ukośnik odwrotny|`\\`|
|Cudzysłów|`\"`|
|Apostrof|`\'`|
|znak Unicode|`\DDD`(gdzie `D` wskazuje cyfrę dziesiętną; zakres 000-255; na `\231` przykład = "ç")|
|znak Unicode|`\xHH`(gdzie `H` wskazuje cyfrę szesnastkową; zakres 00-FF; na `\xE7` przykład = "ç")|
|znak Unicode|`\uHHHH`(UTF-16) (gdzie `H` wskazuje cyfrę szesnastkową; zakres 0000-FFFF;  na przykład `\u00E7` = "ç")|
|znak Unicode|`\U00HHHHHH`(UTF-32) (gdzie `H` wskazuje cyfrę szesnastkową; zakres 000000-10FFFF;  na przykład `\U0001F47D` = "👽")|

> [!IMPORTANT]
> Sekwencja `\DDD` ucieczki jest notacją dziesiętną, a nie notacją ósemkową, taką jak w większości innych języków. W związku z `8` `9` `\040`tym cyfry i są prawidłowe, a sekwencja reprezentuje spację (U + 0020), natomiast ten sam punkt kodu w notacji ósemkowej będzie. `\032`

> [!NOTE]
> Są ograniczone do zakresu 0-255 (0xFF), `\DDD` a `\x` sekwencje ucieczki są efektywnie zestawem znaków [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , ponieważ dopasowuje pierwsze 256 punktów kodowych Unicode.

Jeśli poprzedzany przez symbol @, literał jest ciągiem Verbatim. Oznacza to, że wszystkie sekwencje ucieczki są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.

Ponadto ciąg może być ujęty w potrójne cudzysłowy. W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu. Aby określić ciąg zawierający osadzony ciąg ujęty w cudzysłów, można użyć ciągu Verbatim lub ciągu z potrójnym cudzysłowem. W przypadku używania ciągu Verbatim należy określić dwa znaki cudzysłowu, aby wskazać znak pojedynczego cudzysłowu. Jeśli używasz ciągu z potrójnym cudzysłowem, możesz użyć znaków pojedynczego cudzysłowu bez ich analizowania jako końca ciągu. Ta technika może być przydatna podczas pracy z danymi XML lub innymi strukturami, które zawierają osadzone znaki cudzysłowu.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

W kodzie, ciągi, które mają podziały wierszy są akceptowane, a podziały wierszy są interpretowane dosłownie jako znaki nowego wiersza, chyba że znak ukośnika odwrotnego jest ostatnim znakiem przed przerwaniem. Wiodący biały znak w następnym wierszu jest ignorowany, gdy jest używany ukośnik odwrotny. Poniższy kod generuje `str1` ciąg, który ma wartość `"abc\ndef"` i ciąg `str2` , który ma wartość `"abcdef"`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Można uzyskać dostęp do pojedynczych znaków w ciągu za pomocą składni podobnej do tablicy, jak pokazano poniżej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Dane wyjściowe to `b`.

Lub można wyodrębnić podciągi przy użyciu składni wycinka tablicy, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Dane wyjściowe są następujące:

```
abc
def
```

Ciągi ASCII można reprezentować według tablic bajtów `byte[]`bez znaku. Należy dodać sufiks `B` do literału ciągu, aby wskazać, że jest to ciąg ASCII. Literały ciągu ASCII używane z tablicami bajtowymi obsługują te same sekwencje unikowe co ciągi Unicode, z wyjątkiem sekwencji unikowych Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operatory ciągów

Istnieją dwa sposoby łączenia ciągów: przy użyciu `+` operatora lub `^` operatora. `+` Operator zachowuje zgodność z funkcjami obsługi ciągów .NET Framework.

Poniższy przykład ilustruje łączenie ciągów.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String — Klasa

Ponieważ typ ciągu w jest F# w rzeczywistości `System.String` typem .NET Framework `System.String` , wszystkie elementy członkowskie są dostępne. Obejmuje `+` operator, który jest używany do łączenia ciągów `Length` , właściwość i `Chars` właściwość, która zwraca ciąg jako tablicę znaków Unicode. Aby uzyskać więcej informacji na temat ciągów `System.String`, zobacz.

Za pomocą `Chars` `System.String`właściwości, można uzyskać dostęp do poszczególnych znaków w ciągu, określając indeks, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Moduł String

Dodatkowe funkcje obsługi ciągów są zawarte w `String` module `FSharp.Core` w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [moduł Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
