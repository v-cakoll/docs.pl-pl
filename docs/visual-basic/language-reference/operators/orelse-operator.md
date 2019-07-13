---
title: OrElse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860142"
---
# <a name="orelse-operator-visual-basic"></a>OrElse — Operator (Visual Basic)
Wykonuje łączną sumę logiczną na dwóch wyrażeniach zwarcie.  
  
## <a name="syntax"></a>Składnia  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagane. Wszelkie `Boolean` wyrażenia.  
  
 `expression1`  
 Wymagana. Wszelkie `Boolean` wyrażenia.  
  
 `expression2`  
 Wymagana. Wszelkie `Boolean` wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest nazywany *zwarcie* Jeśli skompilowany kod może obejść przedziały oceny jedno wyrażenie w zależności od wyniku innego wyrażenia. Jeśli wynik pierwsze wyrażenie obliczane określi ostateczny wynik operacji, nie ma potrzeby do oceny, drugie wyrażenie, ponieważ nie można zmienić, wynik końcowy. Zwarcie może poprawić wydajność, jeśli pominięto wyrażenie jest złożone, czy obejmuje wywołania procedur.  
  
 Jeśli do jednego lub obu tych wyrażeń `True`, `result` jest `True`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(nie oceniono)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Typy danych  
 `OrElse` Operator jest zdefiniowany tylko w przypadku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic konwertuje każdy argument konieczny do `Boolean` przed obliczając wartość wyrażenia. Jeśli wynik jest przypisany do typu numerycznego, Visual Basic konwertuje go z `Boolean` do tego typu tak, aby `False` staje się `0` i `True` staje się `-1`.
Aby uzyskać więcej informacji, zobacz [logiczna konwersje typów](../data-types/boolean-data-type.md#type-conversions)
  
## <a name="overloading"></a>Przeciążenie  
 [Operatora Or](../../../visual-basic/language-reference/operators/or-operator.md) i [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) może być *przeciążone*, co oznacza, że klasa lub Struktura można ponownie zdefiniować ich zachowania, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `Or` i `IsTrue` operatory wpływa na zachowanie `OrElse` operatora. Jeśli kod używa `OrElse` dla klasy lub struktury, która przeciążenia `Or` i `IsTrue`, należy zrozumieć ich zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `OrElse` operator przeprowadzić logicznego rozłączenia dwóch wyrażeń. Wynik jest `Boolean` wartość wskazującą, czy jest spełniony jeden z dwóch wyrażeń. Jeśli pierwsze wyrażenie jest `True`, drugi nie jest oceniany.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Poprzedni przykład generuje wyniki `True`, `True`, i `False` odpowiednio. Podczas obliczania `firstCheck`, drugie wyrażenie nie jest oceniany, ponieważ pierwszy jest już `True`. Jednak drugie wyrażenie jest obliczane w obliczeniach kluczowych `secondCheck`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `If`... `Then` instrukcji zawierającej dwóch wywołań procedur. Jeśli pierwsza zwraca wywołanie `True`, druga procedura nie jest wywoływana. Może to dawać nieoczekiwane wyniki, jeśli druga procedura wykonuje ważne zadania, które powinny być zawsze wykonywane po uruchomieniu tej sekcji kodu.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or, operator](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
