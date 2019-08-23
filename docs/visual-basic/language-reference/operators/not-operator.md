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
ms.openlocfilehash: 29e2b159e4c6261a62e788b537102b9b457fe0c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955822"
---
# <a name="not-operator-visual-basic"></a>Not — Operator (Visual Basic)
Wykonuje logiczne negację `Boolean` wyrażenia lub bitową negację wyrażenia liczbowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagane. Wyrażenie `Boolean` dowolne lub liczbowe.  
  
 `expression`  
 Wymagane. Wyrażenie `Boolean` dowolne lub liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W `Boolean` przypadku wyrażeń w poniższej tabeli pokazano, `result` jak określono.  
  
|Jeśli `expression` jest|Wartość `result` jest|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 W przypadku wyrażeń `Not` liczbowych operator odwraca wartości bitowe dowolnego wyrażenia liczbowego i ustawia odpowiedni bit w `result` zależności od poniższej tabeli.  
  
|Jeśli bit w `expression` jest|Bit w `result` jest|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
## <a name="data-types"></a>Typy danych  
 W przypadku negacji logicznej, typ danych wyniku to `Boolean`. W przypadku negacji bitowej dane wynikowe są takie same, jak `expression`w przypadku. Jeśli jednak wyrażenie ma `Decimal`wartość, wynik jest. `Long`  
  
## <a name="overloading"></a>Przeciążenie  
 Operator może być przeciążony, co oznacza, że Klasa lub struktura może zmienić jego zachowanie, gdy jego operand ma typ tej klasy lub struktury. `Not` Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Not` operatora do wykonywania logiczne negacji `Boolean` dla wyrażenia. Wynik jest `Boolean` wartością, która reprezentuje odwracanie wartości wyrażenia.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Powyższy przykład daje wyniki `False` odpowiednio i. `True`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Not` operatora do wykonywania logicznego negacji poszczególnych bitów wyrażenia liczbowego. Bit w wzorcu wyniku jest ustawiony na odwrotność odpowiedniego bitu we wzorcu operandu, łącznie z bitem znaku.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Powyższy przykład daje wyniki odpowiednio – 11, – 9 i – 7.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
