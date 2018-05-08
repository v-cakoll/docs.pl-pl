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
ms.openlocfilehash: 1ee3c1a5b6089f44742281eb40e2a7e9cb3e2812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="orelse-operator-visual-basic"></a>OrElse — Operator (Visual Basic)
Wykonuje zwarcie łączną sumę logiczną na dwóch wyrażeniach.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` wyrażenia.  
  
 `expression1`  
 Wymagana. Wszelkie `Boolean` wyrażenia.  
  
 `expression2`  
 Wymagana. Wszelkie `Boolean` wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest określany jako *zwarcie* Jeśli skompilowanego kodu można pominąć obliczania jednego wyrażenia w zależności od wyniku innego wyrażenia. Jeśli wynik pierwsze wyrażenie obliczane określa końcowego wyniku operacji, jest niepotrzebna można oszacować wyrażenia drugiego, ponieważ nie można zmienić wynik końcowy. Zwarcie może zwiększyć wydajność, jeśli pominięto wyrażenie jest złożony, czy obejmuje on wywołań procedur.  
  
 Jeśli wynikiem obliczania wyrażenia jednego lub obu tych `True`, `result` jest `True`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(nie jest oceniany)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Typy danych  
 `OrElse` Operator jest zdefiniowana tylko dla [— typ danych logicznych](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic konwertuje każdy argument operacji niezbędny do `Boolean` i wykonuje operację wyłącznie w `Boolean`. Przypisz wynik do typu liczbowego, Visual Basic przekonwertuje go z `Boolean` dla tego typu. Można to osiągnąć nieoczekiwane zachowanie. Na przykład `5 OrElse 12` powoduje `–1` po konwersji na `Integer`.  
  
## <a name="overloading"></a>Przeciążenie  
 [Lub Operator](../../../visual-basic/language-reference/operators/or-operator.md) i [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury można zmienić ich zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `Or` i `IsTrue` operatory wpływa na działanie `OrElse` operatora. Jeśli używa Twój kod `OrElse` na klasę lub strukturę, która overloads `Or` i `IsTrue`, trzeba koniecznie zapoznać się ich zachowanie ponownie zdefiniowany. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `OrElse` operatora, aby wykonać logicznego rozłączenia dwóch wyrażeń. Wynik jest `Boolean` wartość wskazującą, czy jest spełniony jeden z dwóch wyrażeń. Jeśli pierwsze wyrażenie jest `True`, drugie nie jest obliczane.  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 Powyższy przykład produkuje wyniki `True`, `True`, i `False` odpowiednio. Podczas obliczania `firstCheck`, drugie wyrażenie nie jest oceniany, ponieważ pierwszy jest już `True`. Jednak drugie wyrażenie jest obliczane w obliczeniach `secondCheck`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `If`... `Then` instrukcja zawierająca dwa wywołań procedur. Jeśli na pierwszym wywołaniu zwraca `True`, druga procedura nie jest wywoływany. Może to powodować nieoczekiwane rezultaty, gdy druga procedura, wykonuje ważne zadania, które powinny być zawsze wykonywane po uruchomieniu tej sekcji kodu.  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Or, operator](../../../visual-basic/language-reference/operators/or-operator.md)  
 [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
