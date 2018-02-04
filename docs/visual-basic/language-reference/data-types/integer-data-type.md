---
title: "Integer — Typ danych (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba700cac58c96b3d6d2f5ed3c74fdd7e95761352
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="integer-data-type-visual-basic"></a>Integer — typ danych (Visual Basic)
Przechowuje 32-bitowe (4-bajtowe) liczby całkowite ze znakiem z zakresu wartości od -2 147 483,648 do 2 147 483 647.  
  
## <a name="remarks"></a>Uwagi
 `Integer` — Typ danych zapewnia optymalną wydajność w 32-bitowego procesora. Inne typy całkowitoliczbowe wolniej wczytują się z pamięci i są w niej zapisywane.  
  
 Wartość domyślna `Integer` ma wartość 0.  

## <a name="literal-assignments"></a>Przydziały literału

Można zadeklarować i zainicjuj `Integer` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny. Jeśli liczba całkowita literału jest poza zakresem `Integer` (to znaczy, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 16,342, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `Integer` wartości.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `I` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Integer` typu danych, jak przedstawiono na poniższym przykładzie.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Porady dotyczące programowania

-   **Zagadnienia dotyczące współdziałania.** Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, takich jak obiekty automatyzacji lub COM, należy pamiętać, że `Integer` ma szerokość różnych danych (16 bitów) w innych środowiskach. Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `Short` zamiast `Integer` w nowy kod Visual Basic.  
  
-   **Rozszerzanie.** `Integer` Rozszerzenie typu danych do `Long`, `Decimal`, `Single`, lub `Double`. Oznacza to, że można przekonwertować `Integer` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Znak literalny typu dołączanie `I` do literału wymusza `Integer` — typ danych. Dołączanie znak typu identyfikator `%` dla wszystkich identyfikatorów wymusza `Integer`.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Int32?displayProperty=nameWithType> struktury.  
  
## <a name="range"></a>Zakres

Jeśli spróbujesz ustawić zmienną typu całkowitoliczbowego na liczbę spoza zakresu dla tego typu, wystąpi błąd. Jeśli spróbujesz ustawić ją na ułamek, liczba jest zaokrąglana w górę lub w dół do najbliższej wartości liczby całkowitej. Jeśli liczba jest jednakowo blisko dwóch wartości całkowitych, wartość jest zaokrąglana do najbliższej parzystej liczby całkowitej. To zachowanie minimalizuje błędy zaokrągleń, które powstają w wyniku konsekwentnego zaokrąglania wartości punktu środkowego w jednym kierunku. W poniższym kodzie pokazano przykłady zaokrąglania.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Zobacz także

<xref:System.Int32?displayProperty=nameWithType>   
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
