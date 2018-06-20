---
title: Ciągi (F#)
description: 'Dowiedz się, jak typ "string" języka F # reprezentuje niezmienne tekst sekwencję znaków Unicode.'
ms.date: 05/16/2016
ms.openlocfilehash: 80c08f5b768dd826745e07b8c5726093050ab730
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207108"
---
# <a name="strings"></a>Ciągi

> [!NOTE]
Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

`string` Typu reprezentuje niezmienne tekst sekwencję znaków Unicode. `string` alias jest `System.String` w programie .NET Framework.

## <a name="remarks"></a>Uwagi
Literały ciągu są rozdzielone znakiem cudzysłowu ("). Znak ukośnika odwrotnego ( \\ ) jest używany do kodowania niektórych znaków specjalnych. Ukośniku odwrotnym i znakiem następnym razem są nazywane *sekwencja unikowa*. Sekwencje obsługiwane w F # ciąg, który w poniższej tabeli przedstawiono literały specjalne.

|Znak|Sekwencja specjalna|
|---------|---------------|
|Backspace|\b|
|Nowy wiersz|\n|
|Powrót karetki|\r|
|Tab|\t|
|ukośnik odwrotny|\\|
|Znak cudzysłowu|\"|
|Apostrof|\'|
|znak Unicode|\u*XXXX* lub \U*XXXXXXXX* (gdzie *X* oznacza cyfrę szesnastkową)|

Jeśli poprzedzone symbolem @ literału jest ciągu dosłownego wyrażenia. Oznacza to, że wszystkie sekwencje specjalne są ignorowane, z wyjątkiem tego, że dwa znaki cudzysłowu są interpretowane jako jeden znak cudzysłowu.

Ponadto ciąg może być ujęta w cudzysłów Potrójna. W takim przypadku wszystkie sekwencje specjalne są ignorowane, łącznie ze znakami cudzysłowu. Aby określić ciąg, który zawiera osadzony jako ciąg, możesz użyć ciągu dosłownego wyrażenia lub ciąg potrójne cudzysłowy. Jeśli używasz ciągu dosłownego wyrażenia, należy określić dwóch znaków cudzysłowu do wskazywania znak pojedynczego cudzysłowu. Użycie ciągu potrójne cudzysłowy, można użyć znaków pojedynczego cudzysłowu bez nich przeanalizowany jako końca ciągu. Ta technika może być przydatne podczas pracy z XML lub inne struktury, które osadzonych znaków cudzysłowu.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

W kodzie ciągów, które mają podziały wierszy są akceptowane i podziały wierszy są interpretowane jako literału jako newlines, chyba że ostatni znak przed podział wiersza jest ukośnikiem odwrotnym. Spacje wiodące w następnym wierszu jest ignorowane, gdy jest używany znak ukośnika odwrotnego. Poniższy kod tworzy ciąg `str1` wartością `"abc\n     def"` i ciąg `str2` wartością `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Można uzyskać dostępu do poszczególnych znaków w ciągu za pomocą składni tablicy w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Dane wyjściowe `b`.

Lub może wyodrębnić podciągów przy użyciu składni wycinek tablicy, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Dane wyjściowe są następujące:

```
abc
def
```

Ciągi ASCII może reprezentować przez tablice bajtów bez znaku, typ `byte[]`. Dodaj sufiks `B` z ciągiem literału, aby wskazać, że ciąg znaków ASCII. Literały ciągu ASCII używane z tablic bajtowych obsługuje tej samej sekwencji unikowych jako ciągów Unicode, z wyjątkiem sekwencje specjalne Unicode.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a>Operatory ciągów
Istnieją dwa sposoby ciągów: za pomocą `+` operator lub za pomocą `^` operatora. `+` Operator zachowuje zgodność z obsługi funkcji ciągów .NET Framework.

Poniższy przykład przedstawia ciągów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a>String — klasa
Ponieważ typ ciągu w języku F # jest rzeczywiście .NET Framework `System.String` wpisz wszystkie `System.String` elementy są dostępne. Obejmuje to `+` operatora, który jest używany do łączenia ciągów, `Length` właściwości oraz `Chars` właściwość, która zwraca ciąg w formie tablicy znaków Unicode. Aby uzyskać więcej informacji na temat ciągów, zobacz `System.String`.

Za pomocą `Chars` właściwość `System.String`, dostęp do poszczególnych znaków w ciągu, określając indeksu, jak to pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a>Moduł ciągu
Dodatkowe funkcje obsługi ciągu znajduje się w `String` modułu w `FSharp.Core` przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Core.String — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)
