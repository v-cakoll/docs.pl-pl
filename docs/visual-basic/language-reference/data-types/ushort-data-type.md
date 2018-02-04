---
title: "UShort — Typ danych (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 958c7c74822d3b5cb311d22977b1b1f8bda04cd7
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="ushort-data-type-visual-basic"></a>Ushort — typ danych (Visual Basic)

Blokad 16-bitowych (2-bajtowych) liczb całkowitych bez znaku z zakresu od 0 do 65 535.  
  
## <a name="remarks"></a>Uwagi

 Użyj `UShort` — typ danych zawierający dane binarne zbyt duży dla `Byte`.  
  
 Wartość domyślna `UShort` ma wartość 0.  

# <a name="literal-assignments"></a>Przydziały literału

Można zadeklarować i zainicjuj `UShort` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny. Jeśli liczba całkowita literału jest poza zakresem `UShort` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 65,034, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `UShort` wartości.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `US` lub `us` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `UShort` typu danych, jak przedstawiono na poniższym przykładzie.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Porady dotyczące programowania
  
-   **Wartości ujemne.** Ponieważ `UShort` jest typu unsigned, nie może reprezentować wartość ujemną. Jeśli używasz jednoargumentowy minus (`-`) operator na wyrażenie obliczane do typu `UShort`, Visual Basic konwertuje wyrażenie `Integer` pierwszy.  
  
-   **Zgodności ze specyfikacją CLS.** `UShort` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.
  
-   **Rozszerzanie.** `UShort` Rozszerzenie typu danych do `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, i `Double`. Oznacza to, że można przekonwertować `UShort` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Znaki literalne dołączanie `US` do literału wymusza `UShort` — typ danych. `UShort`nie ma identyfikatora typu znaku.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.UInt16?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.UInt16>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
