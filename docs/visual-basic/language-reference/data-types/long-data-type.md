---
title: Long — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 687c235be76ef522758658fd1c5fe0cb1dbeb414
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="long-data-type-visual-basic"></a>Long — typ danych (Visual Basic)

Blokad podpisane liczby całkowite (8-bajtowych) 64-bitowym z zakresu od-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807 (9.2... E + 18).  
  
## <a name="remarks"></a>Uwagi

 Użyj `Long` typu danych, aby zawierała liczby całkowite, które są za duże, aby zmieścić ją w `Integer` — typ danych.  
  
 Wartość domyślna `Long` ma wartość 0.

## <a name="literal-assignments"></a>Przydziały literału 

Można zadeklarować i zainicjuj `Long` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny. Jeśli liczba całkowita literału jest poza zakresem `Long` (to znaczy, jeśli jest mniejszy niż <xref:System.Int64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 4 294 967 296, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `Long` wartości.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `L` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Long` typu danych, jak przedstawiono na poniższym przykładzie.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Porady dotyczące programowania

-   **Zagadnienia dotyczące współdziałania.** Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że `Long` ma szerokość różnych danych (32-bitowy) w innych środowiskach. Jeśli argument 32-bitowej do tych składników, Zadeklaruj ją jako `Integer` zamiast `Long` w nowy kod Visual Basic.  
  
-   **Rozszerzanie.** `Long` Rozszerzenie typu danych do `Decimal`, `Single`, lub `Double`. Oznacza to, że można przekonwertować `Long` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Znak literalny typu dołączanie `L` do literału wymusza `Long` — typ danych. Dołączanie znak typu identyfikator `&` dla wszystkich identyfikatorów wymusza `Long`.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Int64?displayProperty=nameWithType> struktury.  

## <a name="see-also"></a>Zobacz także

<xref:System.Int64>
[Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
[Integer — typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
[Short — typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)   
[Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
[Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
[Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
