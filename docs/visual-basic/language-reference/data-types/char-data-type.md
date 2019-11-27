---
title: Char, typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 1ed5b19a307d094fc1d5a6bb0251c57052dc9bc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344048"
---
# <a name="char-data-type-visual-basic"></a>Char — Typ danych (Visual Basic)

Przechowuje 16-bitowe (2-bajtowe) punkty kodu bez znaku w zakresie wartości z zakresu od 0 do 65535. Każdy *punkt kodu*lub znak, reprezentuje pojedynczy znak Unicode.

## <a name="remarks"></a>Uwagi

Użyj `Char`go typu danych, gdy musisz przechowywać tylko jeden znak i nie potrzebują obciążenia `String`. W niektórych przypadkach można użyć `Char()`, tablicy elementów `Char`, aby przechowywać wiele znaków.

Wartość domyślna `Char` jest znakiem z punktem kodu równym 0.

## <a name="unicode-characters"></a>Znaki Unicode

Pierwsze 128 punktów kodowych (0 – 127) Unicode odpowiada literom i symbolom na standardowej klawiaturze amerykańskiej. Te pierwsze 128 punktów kodowych są takie same jak w zestawie znaków ASCII. Drugie 128 punktów kodowych (128 – 255) reprezentuje znaki specjalne, takie jak litery alfabetu łacińskiego, akcenty, symbole waluty i ułamki. Unicode używa pozostałych punktów kodowych (256-65535) dla wielu różnych symboli, w tym na całym świecie, znaki diakrytyczne i symbole matematyczne i techniczne.

Aby określić swoją klasyfikację Unicode, można użyć metod, takich jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na zmiennej `Char`.

## <a name="type-conversions"></a>Konwersje typu

Visual Basic nie są konwertowane bezpośrednio między `Char` i typami liczbowymi. Można użyć funkcji <xref:Microsoft.VisualBasic.Strings.Asc%2A> lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> do przekonwertowania wartości `Char` na `Integer`, która reprezentuje swój punkt kodu. Można użyć funkcji <xref:Microsoft.VisualBasic.Strings.Chr%2A> lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> do przekonwertowania wartości `Integer` na `Char`, który ma ten punkt kodu.

Jeśli przełącznik sprawdzania typu ( [instrukcja Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączona, należy dołączyć znak literału typu do literału ciągu pojedynczego znaku, aby zidentyfikować go jako typ danych `Char`. Ilustruje to poniższy przykład. Pierwsze przypisanie do zmiennej `charVar` generuje błąd kompilatora [BC30512](../../misc/bc30512.md) , ponieważ `Option Strict` jest włączony. Druga kompilacja powiodła się, ponieważ `c` znak typu literału identyfikuje literał jako wartość `Char`ą.

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a>Porady dla programistów

- **Liczby ujemne.** `Char` jest typem bez znaku i nie może reprezentować wartości ujemnej. W każdym przypadku nie należy używać `Char` do przechowywania wartości liczbowych.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli interfejs zawiera składniki, które nie są przeznaczone dla .NET Framework, na przykład obiekty Automation lub COM, należy pamiętać, że typy znaków mają różną szerokość danych (8 bitów) w innych środowiskach. W przypadku przekazania do takiego składnika argumentu 8-bitowego należy zadeklarować go jako `Byte` zamiast `Char` w nowym kodzie Visual Basic.

- **Rozszerzającą.** Typ danych `Char` poszerza do `String`. Oznacza to, że można skonwertować `Char` na `String` i nie będzie napotykać <xref:System.OverflowException?displayProperty=nameWithType>.

- **Znaki typu.** Dołączanie znaku typu literału `C` do literału ciągu pojedynczego znaku wymusza go do `Char` typu danych. `Char` nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.Char?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [String, typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
