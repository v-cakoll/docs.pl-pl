---
title: Boolean Data Type (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 00f77fe5e98099868e02d74fe1adc7690cb95cca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590280"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean Data Type (Visual Basic)
Wartości blokad, które mogą być tylko `True` lub `False`. Słowa kluczowe `True` i `False` odpowiadają dwa stany `Boolean` zmiennych.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [typu Boolean danych (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) zawierają wartości dwustanowy, takie jak PRAWDA/FAŁSZ tak/nie lub Wł. / wył.  
  
 Wartość domyślna `Boolean` jest `False`.  
  
 `Boolean` wartości nie są przechowywane jako liczby, a nie mają równoważne numery przechowywane wartości. Nigdy nie powinien pisania kodu, który polega na równoważne wartości numerycznych `True` i `False`. Jeśli to możliwe, należy ograniczyć użycie `Boolean` zmienne do wartości logiczne, dla których są przeznaczone.  
  
## <a name="type-conversions"></a>Konwersje typu  
 Gdy Visual Basic konwertuje wartości typu danych liczbowych `Boolean`, staje się 0 `False` i stać się wszystkie inne wartości `True`. Gdy konwertuje Visual Basic `Boolean` wartości na typy liczbowe `False` staje się 0 i `True` staje się wartość -1.  
  
 Podczas konwertowania między `Boolean` wartości i numeryczne typy danych, należy pamiętać, że metody konwersji .NET Framework nie zawsze utworzyć takie same wyniki jak słowa kluczowe konwersji Visual Basic. Jest to spowodowane konwersji Visual Basic zachowuje zachowania zgodność z poprzednimi wersjami. Aby uzyskać więcej informacji, zobacz "Boolean typu jest nie Konwertuj do liczbowego typu dokładnie" w [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Wartości ujemne.** `Boolean` nie jest typu liczbowego i nie może reprezentować wartość ujemną. W żadnym przypadku nie należy używać `Boolean` do przechowywania wartości liczbowych.  
  
-   **Znaki typu.** `Boolean` nie ma znak literalny typu ani znak typu identyfikator.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Boolean?displayProperty=nameWithType> struktury.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `runningVB` jest `Boolean` zmiennej, która przechowuje prostą ustawienie tak/nie.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
