---
title: And — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913170"
---
# <a name="and-operator-visual-basic"></a>And — Operator (Visual Basic)
Wykonuje logiczną koniunkcję w dwóch `Boolean` wyrażeniach lub bitowego połączenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wyrażenie `Boolean` dowolne lub liczbowe. W przypadku porównania `result` logicznego jest koniunkcja logiczna dwóch `Boolean` wartości. W przypadku operacji `result` bitowych jest wartością liczbową reprezentującą bitowe połączenia dwóch wzorców bitowych liczb.  
  
 `expression1`  
 Wymagana. Wyrażenie `Boolean` dowolne lub liczbowe.  
  
 `expression2`  
 Wymagany. Wyrażenie `Boolean` dowolne lub liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 `result` W przypadku porównania wartości logicznych `True` jest if i tylko wtedy `expression1` , `expression2` gdy oba `True`i są oceniane do. W poniższej tabeli przedstawiono sposób `result` określania.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> W porównaniu `And` wartości logicznej operator zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur. [Operator AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *krótkie obwody*, co oznacza, że `expression1` jeśli jest `False`, `expression2` to nie jest oceniane.  
  
 W przypadku zastosowania do wartości `And` numerycznych operator wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zależności od poniższej tabeli.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wyniki.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego `Boolean` wyrażenia i jednego wyrażenia liczbowego, Visual Basic `Boolean` konwertuje wyrażenie na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.  
  
 W przypadku porównania wartości logicznych typem danych wyniku jest `Boolean`. W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów `expression1` danych i. `expression2` Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
> Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `And` Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `And` operatora do wykonywania logicznego połączenia dwóch wyrażeń. Wynik jest `Boolean` wartością, która reprezentuje, czy oba wyrażenia są `True`.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Powyższy przykład daje wyniki `True` odpowiednio i. `False`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `And` operatora do wykonywania logicznego połączenia na poszczególnych bitach dwóch wyrażeń liczbowych. Bit w wzorcu wyniku jest ustawiany, jeśli odpowiadające im bity w operandach są ustawione na 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Poprzedni przykład daje wyniki odpowiednio 8, 2 i 0.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso, operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
