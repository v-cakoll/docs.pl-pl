---
title: Ciągi
description: Dowiedz się, jak typ "string" języka F# reprezentuje niezmienny tekst jako sekwencję znaków Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739572"
---
# <a name="strings"></a>Ciągi

> [!NOTE]
> Łącza odwołania interfejsu API w tym artykule spowoduje, że przejdziesz do usługi MSDN.  Odwołanie docs.microsoft.com interfejsu API nie jest kompletne.

Typ `string` reprezentuje niezmienny tekst jako sekwencję znaków Unicode. `string`jest aliasem `System.String` w ramach .NET Framework.

## <a name="remarks"></a>Uwagi

Literały ciągów są rozdzielane znakiem cudzysłowu ("). Znak ukośnika \\ odwrotnego ( ) służy do kodowania niektórych znaków specjalnych. Ukośnik odwrotny i następny znak razem są znane jako *sekwencja ucieczki*. Sekwencje ucieczki obsługiwane w literałach ciągu F# są wyświetlane w poniższej tabeli.

|Znak|Sekwencja ucieczki|
|---------|---------------|
|Alerty|`\a`|
|Backspace|`\b`|
|Pasza formularza|`\f`|
|Newline|`\n`|
|Powrót karetki|`\r`|
|Tab|`\t`|
|Zakładka Pionowa|`\v`|
|Ukośnik odwrotny|`\\`|
|Cudzysłowu|`\"`|
|Apostrof|`\'`|
|znak Unicode|`\DDD`(gdzie `D` wskazuje cyfrę dziesiętną; zakres od 000 do 255; na przykład `\231` = "ç")|
|znak Unicode|`\xHH`(gdzie `H` wskazuje cyfrę szesnastową; zakres 00 - `\xE7` FF; na przykład = "ç")|
|znak Unicode|`\uHHHH`(UTF-16) (gdzie `H` wskazuje cyfrę szesnastową; zakres 0000 - FFFF;  na przykład `\u00E7` = "ç")|
|znak Unicode|`\U00HHHHHH`(UTF-32) (gdzie `H` wskazuje cyfrę szesnastową; zakres 000000 - 10FFFF;  na przykład `\U0001F47D` =👽" ")|

> [!IMPORTANT]
> Sekwencja `\DDD` ucieczki jest notacją dziesiętną, a nie notacją ósemkową, jak w większości innych języków. W związku z `8` `9` tym cyfry i `\032` są prawidłowe, a sekwencja reprezentuje spację (U + 0020), podczas gdy ten sam punkt kodu w notacji ósemkowej będzie `\040`.

> [!NOTE]
> Są ograniczone do zakresu od 0 - 255 (0xFF), `\DDD` i `\x` sekwencje ucieczki są skutecznie [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) zestaw znaków, ponieważ pasuje do pierwszych 256 punktów kodu Unicode.

## <a name="verbatim-strings"></a>Dosłownie ciągi

Jeśli poprzedzone symbol @, literał jest ciągiem dosłownie. Oznacza to, że wszystkie sekwencje unikowe są ignorowane, z tą różnicą, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.

## <a name="triple-quoted-strings"></a>Potrójne notowane ciągi

Ponadto ciąg może być ujęty potrójnymi cudzysłowami. W takim przypadku wszystkie sekwencje ucieczki są ignorowane, w tym znaki podwójnego cudzysłowu. Aby określić ciąg, który zawiera osadzony ciąg cudzysłowu, można użyć ciągu dosłownie lub ciągu potrójnego. W przypadku użycia ciągu dosłownego należy określić dwa znaki cudzysłowu, aby wskazać pojedynczy znak cudzysłowu. Jeśli używasz potrójnego ciągu, można użyć pojedynczych znaków cudzysłowu bez ich analizowania jako końca ciągu. Ta technika może być przydatna podczas pracy z xml lub innymi strukturami, które zawierają osadzone cudzysłowy.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

W kodzie ciągi, które mają podziały wierszy są akceptowane, a podziały wierszy są interpretowane dosłownie jako nowe linie, chyba że znak ukośnika odwrotnego jest ostatnim znakiem przed podziałem wiersza. Początkowa biały znak w następnym wierszu jest ignorowana, gdy używany jest znak ukośnika odwrotnego. Poniższy kod tworzy `str1` ciąg, `"abc\ndef"` który ma `str2` wartość `"abcdef"`i ciąg, który ma wartość .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Indeksowanie ciągów i krojenie

Dostęp do poszczególnych znaków w ciągu można uzyskać przy użyciu składni podobnej do tablicy, w następujący sposób.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Wyjście jest `b`.

Można też wyodrębnić podciągi przy użyciu składni plasterka tablicy, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Dane wyjściowe są następujące:

```console
abc
def
```

Ciągi ASCII można reprezentować według tablic niepodpisanych bajtów, wpisz `byte[]`. Sufiks `B` można dodać do literału ciągu, aby wskazać, że jest to ciąg ASCII. Literały ciągu ASCII używane z tablicami bajtowymi obsługują te same sekwencje ucieczki co ciągi Unicode, z wyjątkiem sekwencji unikowych Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operatory ciągów

Operator `+` może służyć do łączenia ciągów, zachowując zgodność z funkcjami obsługi ciągów .NET Framework. Poniższy przykład ilustruje łączenie ciągów.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Klasa ciągu

Ponieważ typ ciągu w języku F# `System.String` jest faktycznie `System.String` typem .NET Framework, wszystkie elementy członkowskie są dostępne. Obejmuje to `+` operator, który jest używany do łączenia ciągów, `Length` właściwości i `Chars` właściwości, która zwraca ciąg jako tablicę znaków Unicode. Aby uzyskać więcej informacji `System.String`na temat ciągów, zobacz .

Za pomocą `Chars` właściwości `System.String`, można uzyskać dostęp do poszczególnych znaków w ciągu, określając indeks, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Moduł ciągów

Dodatkowe funkcje obsługi ciągów znajduje `String` się `FSharp.Core` w module w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
