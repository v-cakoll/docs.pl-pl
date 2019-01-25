---
title: Not — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: cd93316ada1fcf0997922f71a8efc5a3cf411d09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614617"
---
# <a name="not-operator-visual-basic"></a>Not — Operator (Visual Basic)
Wykonuje logiczną negację na `Boolean` wyrażenie lub bitowego zaprzeczenia wyrażenia liczbowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać `Boolean` wyrażenia, w poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression` jest|Wartość `result` jest|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Dla wyrażeń liczbowych `Not` operator odwraca wartości bitowe dowolne wyrażenie numeryczne i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression` jest|Bit w `result` jest|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
## <a name="data-types"></a>Typy danych  
 Logiczna Negacja, typ danych wyniku jest `Boolean`. Dla Negacja, typ danych wyniku jest taka sama, jak w przypadku `expression`. Jednakże jeśli wyrażenie ma `Decimal`, wynik jest `Long`.  
  
## <a name="overloading"></a>Przeciążenie  
 `Not` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie podczas jej argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Not` operator do przeprowadzania Negacja logiczna `Boolean` wyrażenia. Wynik jest `Boolean` wartość, która reprezentuje odwrotnej wartość wyrażenia.  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 Poprzedni przykład generuje wyniki `False` i `True`, odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Not` operator przeprowadzić Negacja logiczna pojedynczych bitów wyrażenia liczbowego. Bit we wzorcu wynik jest ustawiony do tyłu odnośny bit we wzorcu operand, łącznie z bitem.  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 Poprzedni przykład generuje wyniki – 11, –9 i –7, odpowiednio.  
  
## <a name="see-also"></a>Zobacz także
- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
