---
title: Or — Operator
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348252"
---
# <a name="or-operator-visual-basic"></a>Or — Operator (Visual Basic)
Wykonuje logiczne rozłączenie dwóch wyrażeń `Boolean` lub bitowego rozłączenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Dowolne `Boolean` lub wyrażenie liczbowe. W przypadku porównania `Boolean` `result` jest łącznym logicznym rozłączeniem dwóch wartości `Boolean`. W przypadku operacji bitowych `result` jest wartością liczbową reprezentującą łączny czas rozłączenia dwóch wzorców bitowych liczbowych.  
  
 `expression1`  
 Wymagana. Dowolne `Boolean` lub wyrażenie liczbowe.  
  
 `expression2`  
 Wymagana. Dowolne `Boolean` lub wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku porównania `Boolean` `result` jest `False` Jeśli i tylko wtedy, gdy obie `expression1` i `expression2` będą oceniane do `False`. W poniższej tabeli przedstawiono sposób określania `result`.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> W porównaniu `Boolean` operator `Or` zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur. [Operator OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje *krótkie obobwódanie*, co oznacza, że jeśli `expression1` jest `True`, `expression2` nie jest oceniane.  
  
 W przypadku operacji bitowych operator `Or` wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego wyrażenia `Boolean` i jednego wyrażenia liczbowego, Visual Basic konwertuje wyrażenie `Boolean` na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.  
  
 W przypadku porównania `Boolean` typ danych wyniku jest `Boolean`. W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2`. Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 Operator `Or` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `Or`, aby wykonać łączne logiczne rozłączenie dwóch wyrażeń. Wynikiem jest `Boolean` wartość, która reprezentuje, czy jeden z dwóch wyrażeń jest `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Poprzedni przykład generuje odpowiednio wyniki `True`, `True`i `False`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `Or`, aby wykonać łączne logiczne rozłączenie dla poszczególnych bitów dwóch wyrażeń liczbowych. Bit w wzorcu wyniku jest ustawiany, jeśli jeden z odpowiednich bitów w operandach jest ustawiony na 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Powyższy przykład daje wyniki odpowiednio 10, 14 i 14.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse, operator](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
