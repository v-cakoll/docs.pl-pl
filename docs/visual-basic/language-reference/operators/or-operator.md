---
title: Or — Operator (Visual Basic)
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
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955839"
---
# <a name="or-operator-visual-basic"></a>Or — Operator (Visual Basic)
Wykonuje logiczne rozłączenie dwóch `Boolean` wyrażeń lub bitowego rozłączenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagane. Wyrażenie `Boolean` dowolne lub liczbowe. W `Boolean` przypadku `result` porównania jest to łączne logiczne rozłączenie `Boolean` dwóch wartości. W przypadku operacji `result` bitowych jest wartością liczbową reprezentującą łączny czas rozłączenia dwóch wzorców bitowych liczbowych.  
  
 `expression1`  
 Wymagane. Wyrażenie `Boolean` dowolne lub liczbowe.  
  
 `expression2`  
 Wymagane. Wyrażenie `Boolean` dowolne lub liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W `Boolean` przypadku `False` `expression1` `expression2` porównania ma wartość i tylko wtedy, gdy oba i są oceniane do `False`. `result` W poniższej tabeli przedstawiono sposób `result` określania.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> `Boolean` W porównaniu `Or` operator zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur. [Operator OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje *krótkie obwody*, co oznacza, że `expression1` jeśli jest `True`, `expression2` to nie jest oceniane.  
  
 W przypadku operacji `Or` bitowych operator wykonuje bitowe porównanie identycznie ustawionych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zależności od poniższej tabeli.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego `Boolean` wyrażenia i jednego wyrażenia liczbowego, Visual Basic `Boolean` konwertuje wyrażenie na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.  
  
 Dla porównania, typ danych `Boolean`wyniku. `Boolean` W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów `expression1` danych i. `expression2` Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `Or` Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `Or` aby wykonać łączne logiczne rozłączenie dwóch wyrażeń. Wynik jest `Boolean` wartością, która reprezentuje, czy jedno z dwóch wyrażeń jest `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Powyższy przykład daje wyniki `True`, `True`i `False`, odpowiednio.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `Or` aby wykonać łączne logiczne rozłączenie dla poszczególnych bitów dwóch wyrażeń liczbowych. Bit w wzorcu wyniku jest ustawiany, jeśli jeden z odpowiednich bitów w operandach jest ustawiony na 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Powyższy przykład daje wyniki odpowiednio 10, 14 i 14.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse, operator](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
