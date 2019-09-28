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
ms.openlocfilehash: bd6ebbf5f53a7cf187b5d8ce7630080d44d46df2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591618"
---
# <a name="and-operator-visual-basic"></a>And — Operator (Visual Basic)
Wykonuje logiczne koniunkcje dla dwóch wyrażeń `Boolean` lub bitowego połączenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolny `Boolean` lub wyrażenie liczbowe. W przypadku porównania logicznego `result` jest koniunkcją logiczną dwóch wartości `Boolean`. W przypadku operacji bitowych `result` to wartość liczbowa reprezentująca bitowe połączenia dwóch wzorców bitowych liczb.  
  
 `expression1`  
 Wymagany. Dowolny `Boolean` lub wyrażenie liczbowe.  
  
 `expression2`  
 Wymagany. Dowolny `Boolean` lub wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku porównania logicznego wartość `result` jest `True`, jeśli i tylko wtedy, gdy obie `expression1` i `expression2` są oceniane do `True`. W poniższej tabeli przedstawiono sposób określania `result`.  
  
|Jeśli `expression1` to|I `expression2` jest|Wartość `result` to|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> W porównaniu wartości logicznej operator `And` zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur. [Operator AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *krótkie obwody*, co oznacza, że jeśli `expression1` jest `False`, wówczas `expression2` nie jest oceniane.  
  
 W przypadku zastosowania do wartości numerycznych operator `And` wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` to|Bit w `result` to|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wyniki.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego wyrażenia `Boolean` i jednego wyrażenia liczbowego, Visual Basic konwertuje wyrażenie `Boolean` na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.  
  
 W przypadku porównania wartości logicznych typem danych wyniku jest `Boolean`. W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2`. Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
> Operator `And` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `And` do wykonywania logicznego połączenia dwóch wyrażeń. Wynikiem jest wartość `Boolean`, która reprezentuje, czy oba wyrażenia są `True`.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Powyższy przykład daje wyniki odpowiednio dla `True` i `False`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `And` do wykonywania logicznego połączenia na poszczególnych bitach dwóch wyrażeń liczbowych. Bit w wzorcu wyniku jest ustawiany, jeśli odpowiadające im bity w operandach są ustawione na 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Poprzedni przykład daje wyniki odpowiednio 8, 2 i 0.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso, operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
