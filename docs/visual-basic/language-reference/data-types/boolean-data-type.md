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
ms.openlocfilehash: bbd914d8b4239bbae1de7031e68b2900cf5ad6a3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862386"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean Data Type (Visual Basic)
Przechowuje wartości, które mogą być tylko `True` lub `False`. Słowa kluczowe `True` i `False` odpowiadają dwa stany `Boolean` zmiennych.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [typ danych Boolean (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) zawiera wartości dwoma stanami, takie jak PRAWDA/FAŁSZ tak/nie lub włączenia/wyłączenia.  
  
 Wartość domyślna `Boolean` jest `False`.  
  
 `Boolean` wartości nie są przechowywane jako liczby i przechowywane wartości nie są przeznaczone do równoważne liczb. Nigdy nie należy wpisać kod, który opiera się na równoważne wartości liczbowe `True` i `False`. Jeśli to możliwe, należy ograniczyć użycie `Boolean` zmienne do wartości logiczne, dla których są one przeznaczone.  
  
## <a name="type-conversions"></a>Konwersje typu  
 Kiedy Visual Basic konwertuje wartości typu danych liczbowych `Boolean`, staje się 0 `False` i stają się wszystkie inne wartości `True`. Kiedy Visual Basic konwertuje `Boolean` wartości do typów numerycznych, `False` staje się 0 i `True` staje się -1.  
  
 Podczas konwertowania między `Boolean` wartości i typy danych numerycznych, należy pamiętać o tym, że metody konwersji .NET Framework nie zawsze działają tak samo jak słowa kluczowe konwersji języka Visual Basic. Jest to spowodowane konwersji języka Visual Basic zachowuje zgodność z poprzednimi wersjami zachowanie. Aby uzyskać więcej informacji, zobacz "Logiczna typu jest nie Konwertuj do liczbowego typu dokładnie" w [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Liczby ujemne.** `Boolean` nie jest typu liczbowego i nie może reprezentować wartość ujemną. W każdym przypadku, nie należy używać `Boolean` do przechowywania wartości liczbowych.  
  
-   **Znaki typu.** `Boolean` nie ma znak literalny typu lub znak typu identyfikator.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Boolean?displayProperty=nameWithType> struktury.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `runningVB` jest `Boolean` zmienną, która przechowuje prostego ustawienie tak/nie.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
