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
ms.openlocfilehash: ca0f95342783d22559761294ccea6056cd3e4fa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918453"
---
# <a name="long-data-type-visual-basic"></a>Long — typ danych (Visual Basic)

Przechowuje podpisane liczby całkowite (8-bajtową) 64-bitowym z zakresu od-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807 (9.2... E + 18).  
  
## <a name="remarks"></a>Uwagi

 Użyj `Long` typu danych, aby zawierała liczby całkowite, które są zbyt duże, aby zmieścić ją w `Integer` typu danych.  
  
 Wartość domyślna `Long` wynosi 0.

## <a name="literal-assignments"></a>Literał przypisania 

Można zadeklarować i zainicjować `Long` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego. Jeśli literał liczby całkowitej jest poza zakresem `Long` (to znaczy, jeśli jest mniejszy niż <xref:System.Int64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 4 294 967 296, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `Long` wartości.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `L` [wpisz znak](../../programming-guide/language-features/data-types/type-characters.md) do oznaczania `Long` typu danych, co ilustruje poniższy przykład.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, pamiętaj, że `Long` ma różną szerokość danych (32-bitowy) w innych środowiskach. Jeśli przekazujesz 32-bitowy argument do takiego składnika, Zadeklaruj go jako `Integer` zamiast `Long` nowego kodu języka Visual Basic.  
  
- **Rozszerzanie.** `Long` — Typ danych rozszerza się na `Decimal`, `Single`, lub `Double`. Oznacza to, że możesz przekonwertować `Long` do jednej z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaku typu literał `L` do literału wymusza `Long` typu danych. Dołączanie znaku typu identyfikator `&` do jakiegokolwiek identyfikatora wymusza `Long`.  
  
- **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Int64?displayProperty=nameWithType> struktury.  

## <a name="see-also"></a>Zobacz także

- <xref:System.Int64>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
