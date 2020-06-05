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
ms.openlocfilehash: 3dbbf9f6a2c4079775e05f5d2dcd8704c1ec4259
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387481"
---
# <a name="char-data-type-visual-basic"></a>Char — Typ danych (Visual Basic)

Przechowuje 16-bitowe (2-bajtowe) punkty kodu bez znaku w zakresie wartości z zakresu od 0 do 65535. Każdy *punkt kodu*lub znak, reprezentuje pojedynczy znak Unicode.

## <a name="remarks"></a>Uwagi

Użyj `Char` typu danych, gdy musisz przechowywać tylko jeden znak i nie potrzebujesz nakładu pracy `String` . W niektórych przypadkach można użyć `Char()` tablicy `Char` elementów, aby przechowywać wiele znaków.

Wartość domyślna `Char` to znak z punktem kodu równym 0.

## <a name="unicode-characters"></a>Znaki Unicode

Pierwsze 128 punktów kodowych (0 – 127) Unicode odpowiada literom i symbolom na standardowej klawiaturze amerykańskiej. Te pierwsze 128 punktów kodowych są takie same jak w zestawie znaków ASCII. Drugie 128 punktów kodowych (128 – 255) reprezentuje znaki specjalne, takie jak litery alfabetu łacińskiego, akcenty, symbole waluty i ułamki. Unicode używa pozostałych punktów kodowych (256-65535) dla wielu różnych symboli, w tym na całym świecie, znaki diakrytyczne i symbole matematyczne i techniczne.

<xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A> `Char` Aby określić swoją klasyfikację Unicode, można użyć metod takich jak i na zmiennej.

## <a name="type-conversions"></a>Konwersje typu

Visual Basic nie konwertuje bezpośrednio między `Char` i typu liczbowego. Można użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> funkcji lub, <xref:Microsoft.VisualBasic.Strings.AscW%2A> Aby przekonwertować `Char` wartość na `Integer` , która reprezentuje swój punkt kodu. Można użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> funkcji lub, <xref:Microsoft.VisualBasic.Strings.ChrW%2A> Aby przekonwertować `Integer` wartość na `Char` , która ma ten punkt kodu.

Jeśli przełącznik sprawdzania typu ( [instrukcja Option Strict](../statements/option-strict-statement.md)) jest włączona, należy dołączyć znak literału typu do literału ciągu pojedynczego znaku, aby zidentyfikować go jako `Char` Typ danych. Ilustruje to poniższy przykład. Pierwsze przypisanie do `charVar` zmiennej generuje błąd kompilatora [BC30512](../../misc/bc30512.md) , ponieważ `Option Strict` jest on włączony. Druga kompilacja powiodła się, ponieważ `c` znak typu literału identyfikuje literał jako `Char` wartość.

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

- **Liczby ujemne.** `Char`jest typem bez znaku i nie może reprezentować wartości ujemnej. W każdym przypadku nie należy używać `Char` do przechowywania wartości numerycznych.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli interfejs zawiera składniki, które nie są przeznaczone dla .NET Framework, na przykład obiekty Automation lub COM, należy pamiętać, że typy znaków mają różną szerokość danych (8 bitów) w innych środowiskach. W przypadku przekazania do takiego składnika argumentu 8-bitowego należy zadeklarować go jako `Byte` zamiast `Char` w nowym kodzie Visual Basic.

- **Rozszerzającą.** `Char`Typ danych jest rozszerzany do `String` . Oznacza to, że można przeprowadzić konwersję `Char` do `String` i nie napotkasz <xref:System.OverflowException?displayProperty=nameWithType> .

- **Znaki typu.** Dołączanie znaku typu literału `C` do literału ciągu z pojedynczym znakiem wymusza do tego `Char` typu danych. `Char`nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Char?displayProperty=nameWithType> strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Typy danych](index.md)
- [Typ danych ciągu](string-data-type.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Instrukcje: Wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
