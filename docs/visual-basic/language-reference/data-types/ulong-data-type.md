---
title: "ULong — Typ danych (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 606e0ef87b209bb2e75e28223f27d081713c1b7e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="ulong-data-type-visual-basic"></a>Ulong — typ danych (Visual Basic)

Przechowuje 64-bitowych (8-bajtowych) liczb całkowitych bez znaku z zakresu od 0 do 18,446,744,073,709,551,615 (10 razy większa od 1.84 ^ 19).  
  
## <a name="remarks"></a>Uwagi

Użyj `ULong` — typ danych zawierający dane binarne zbyt duży dla `UInteger`, lub największego możliwego podpisane liczby całkowite.  
  
Wartość domyślna `ULong` ma wartość 0.

## <a name="literal-assignments"></a>Przydziały literału

Można zadeklarować i zainicjuj `ULong` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny. Jeśli liczba całkowita literału jest poza zakresem `ULong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `ULong` wartości.
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `UL` lub `ul` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `ULong` typu danych, jak przedstawiono na poniższym przykładzie.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Porady dotyczące programowania
  
-   **Wartości ujemne.** Ponieważ `ULong` jest typu unsigned, nie może reprezentować wartość ujemną. Jeśli używasz jednoargumentowy minus (`-`) operator na wyrażenie obliczane do typu `ULong`, Visual Basic konwertuje wyrażenie `Decimal` pierwszy.  
  
-   **Zgodności ze specyfikacją CLS.** `ULong` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.  
  
-   **Zagadnienia dotyczące współdziałania.** Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy, takich jak `ulong` może mieć szerokość różnych danych (32-bitowy) w innych środowiskach. Jeśli argument 32-bitowej do tych składników, Zadeklaruj ją jako `UInteger` zamiast `ULong` w zarządzanym kodzie języka Visual Basic.  
  
     Ponadto automatyzacji nie obsługuje 64-bitowych liczb całkowitych w systemie Windows 95, Windows 98, Windows ME lub Windows 2000. Nie można przekazać języka Visual Basic `ULong` argument składnika automatyzacji na tych platformach.  
  
-   **Rozszerzanie.** `ULong` Rozszerzenie typu danych do `Decimal`, `Single`, i `Double`. Oznacza to, że można przekonwertować `ULong` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Znaki literalne dołączanie `UL` do literału wymusza `ULong` — typ danych. `ULong`nie ma identyfikatora typu znaku.
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.UInt64?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz także

 <xref:System.UInt64>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
