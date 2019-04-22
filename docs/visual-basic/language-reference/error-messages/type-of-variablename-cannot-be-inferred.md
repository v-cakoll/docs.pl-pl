---
title: Nie można wywnioskować typu elementu „<variablename>”, ponieważ granice pętli i zmienna step nie mogą zostać poszerzone do tego samego typu
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: e90e881546c12df2c8b19ff03a4d4c7304c4596c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815878"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Typ "\<nazwa_zmiennej >" nie można wywnioskować, ponieważ granice pętli i zmienna Step nie mogą zostać poszerzone do tego samego typu
Zostały napisane `For...Next` pętli, w którym kompilator nie można wywnioskować typu danych dla zmienna sterująca pętli, ponieważ są spełnione następujące warunki:  
  
-   Typ danych zmienna sterująca pętli nie zostanie określony z `As` klauzuli.  
  
-   Granice pętli i zmienna zawiera co najmniej dwa typy danych.  
  
-   Nie standardowa występują konwersje między typami danych.  
  
 W związku z tym kompilator nie można wywnioskować typu danych zmienna sterująca pętli.  
  
 W poniższym przykładzie zmienna jest znakiem i granice pętli są oba liczbami całkowitymi. Ponieważ istnieje standardowa konwersja między znakami i liczb całkowitych, ten błąd jest zgłaszany.  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **Identyfikator błędu:** BC30982  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień typy granice pętli i zmienna zgodnie z potrzebami, tak, aby co najmniej jeden z nich to typ, który inne mogą zostać poszerzone do. W poprzednim przykładzie, należy zmienić typ `stepVar` do `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —lub—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Użyj funkcji konwersji jawnej konwertować granice pętli i zmienna na odpowiednie typy. W poprzednim przykładzie, należy zastosować `Val` funkcja `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
