---
title: Char — Typ danych (Visual Basic)
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
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512787"
---
# <a name="char-data-type-visual-basic"></a>Char — Typ danych (Visual Basic)

Przechowuje 16-bitowe (2-bajtowe) punkty kodu bez znaku w zakresie wartości z zakresu od 0 do 65535. Każdy *punkt kodu*lub znak, reprezentuje pojedynczy znak Unicode.

## <a name="remarks"></a>Uwagi

Użyj typu `String`danych, gdy musisz przechowywać tylko jeden znak i nie potrzebujesz nakładu pracy. `Char` W niektórych przypadkach można użyć `Char()` `Char` tablicy elementów, aby przechowywać wiele znaków.

Wartość `Char` domyślna to znak z punktem kodu równym 0.

## <a name="unicode-characters"></a>Znaki Unicode

Pierwsze 128 punktów kodowych (0 – 127) Unicode odpowiada literom i symbolom na standardowej klawiaturze amerykańskiej. Te pierwsze 128 punktów kodowych są takie same jak w zestawie znaków ASCII. Drugie 128 punktów kodowych (128 – 255) reprezentuje znaki specjalne, takie jak litery alfabetu łacińskiego, akcenty, symbole waluty i ułamki. Unicode używa pozostałych punktów kodowych (256-65535) dla wielu różnych symboli, w tym na całym świecie, znaki diakrytyczne i symbole matematyczne i techniczne.

Aby określić swoją klasyfikację <xref:System.Char.IsDigit%2A> Unicode <xref:System.Char.IsPunctuation%2A> , można `Char` użyć metod takich jak i na zmiennej.

## <a name="type-conversions"></a>Konwersje typu

Visual Basic nie konwertuje bezpośrednio między `Char` i typu liczbowego. Można użyć <xref:Microsoft.VisualBasic.Strings.Asc%2A> funkcji lub <xref:Microsoft.VisualBasic.Strings.AscW%2A> , `Char` Aby`Integer` przekonwertować wartość na, która reprezentuje swój punkt kodu. Można użyć <xref:Microsoft.VisualBasic.Strings.Chr%2A> funkcji lub <xref:Microsoft.VisualBasic.Strings.ChrW%2A> , `Integer` Aby`Char` przekonwertować wartość na, która ma ten punkt kodu.

Jeśli przełącznik sprawdzania typu ([instrukcja Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest włączony, należy dołączyć znak literału typu do literału ciągu pojedynczego znaku, aby zidentyfikować go jako `Char` typ danych. Ilustruje to poniższy przykład.

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a>Porady dla programistów

- **Liczby ujemne.** `Char`jest typem bez znaku i nie może reprezentować wartości ujemnej. W każdym przypadku nie należy używać `Char` do przechowywania wartości numerycznych.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli interfejs zawiera składniki, które nie są przeznaczone dla .NET Framework, na przykład obiekty Automation lub COM, należy pamiętać, że typy znaków mają różną szerokość danych (8 bitów) w innych środowiskach. W przypadku przekazania do takiego składnika argumentu 8-bitowego należy zadeklarować go jako `Byte` `Char` zamiast w nowym kodzie Visual Basic.

- **Rozszerzającą.** Typ `Char` danych jest rozszerzany do `String`. Oznacza to, że można `Char` dokonać `String` konwersji do <xref:System.OverflowException?displayProperty=nameWithType> i nie napotkasz błędu.

- **Znaki typu.** Dołączanie znaku `C` typu literału do literału ciągu z pojedynczym znakiem wymusza `Char` do tego typu danych. `Char`nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Char?displayProperty=nameWithType> strukturą.

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
- [Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
