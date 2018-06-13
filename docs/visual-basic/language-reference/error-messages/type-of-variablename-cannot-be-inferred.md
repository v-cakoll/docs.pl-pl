---
title: Typ &#39; &lt;nazwa_zmiennej&gt; &#39; nie można go wywnioskować, ponieważ granice pętli i zmienna krok nie poszerzyć na ten sam typ.
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: d6fdd9445b5336773d150c643c7bf1ca58a0c87a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597155"
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Typ &#39; &lt;nazwa_zmiennej&gt; &#39; nie można go wywnioskować, ponieważ granice pętli i zmienna krok nie poszerzyć na ten sam typ.
Napisano `For...Next` pętli, w którym kompilator nie można wywnioskować typu danych dla zmienna sterująca pętli, ponieważ są spełnione następujące warunki:  
  
-   Typ danych zmienna sterująca pętli nie zostanie określony z `As` klauzuli.  
  
-   Granice pętli i zmienna krok zawiera co najmniej dwóch typów.  
  
-   Istnieje ma standardowych konwersji typów danych.  
  
 W związku z tym kompilator nie można wywnioskować typu danych zmienna sterująca pętli for.  
  
 W poniższym przykładzie zmienna kroku jest znak i granice pętli są obie liczb całkowitych. Ten błąd jest zgłaszany, ponieważ nie istnieje konwersja standardowa między znakami i liczb całkowitych.  
  
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
  
-   Zmień typy granice pętli i zmienna krok w razie potrzeby, tak, aby co najmniej jeden z nich jest typ innych rozszerzane. W poprzednim przykładzie, należy zmienić typ `stepVar` do `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     —lub—  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Użyj konwersji jawnej, aby przekonwertować granice pętli i zmienna krok do odpowiednich typów. W powyższym przykładzie `Val` funkcja `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
