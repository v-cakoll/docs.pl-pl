---
title: And — Operator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e1f9df11152f88ef0db24a794026d6f5888a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="and-operator-visual-basic"></a>And — Operator (Visual Basic)
Wykonuje koniunkcję logiczną na dwóch `Boolean` wyrażeń lub koniunkcję bitową na dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego. Dla porównania Boolean `result` jest logicznego połączenia dwóch `Boolean` wartości. Dla Operacje bitowe `result` wartość liczbową reprezentujący koniunkcję wzorców liczbowych bit dwa.  
  
 `expression1`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression2`  
 Wymagany. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Dla porównania Boolean `result` jest `True` przypadku i tylko wtedy, gdy oba `expression1` i `expression2` obliczać `True`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Logiczna porównania `And` operator zawsze ocenia oba wyrażenia, które mogą obejmować tworzenie wywołań procedur. [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *zwarcie*, co oznacza, że jeśli `expression1` jest `False`, następnie `expression2` nie jest obliczane.  
  
 Po zastosowaniu do wartości numerycznych `And` operator przeprowadza porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiedniej `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bit w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne arytmetyczne operatorów, wszystkie operacje bitowe powinny być ujęte w nawiasy, aby zapewnić dokładne wyniki.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli operandy składają się z jednego `Boolean` wyrażenie i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje operacji.  
  
 Porównanie Boolean, typ danych wyniku jest `Boolean`. Porównanie bitowe, typu danych jest typ liczbowy odpowiednie dla typów danych `expression1` i `expression2`. Znajdują się w tabeli "Relacyjnych i operator porównania" [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  `And` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `And` operatora, aby wykonać koniunkcję logiczną na dwóch wyrażeniach. Wynik jest `Boolean` wartość wskazującą, czy oba wyrażenia są `True`.  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 Powyższy przykład produkuje wyniki `True` i `False`odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `And` operatora, aby wykonać połączenie logiczne na poszczególnych bitów dwóch wyrażeń liczbowych. Bit we wzorcu wynik jest ustawiona, jeśli odpowiednich bitów w operandy zostaną ustawione na 1.  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 Powyższy przykład produkuje wyniki 8, 2 i 0, odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [AndAlso — Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
