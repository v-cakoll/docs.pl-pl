---
title: Operatory porównania w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: 873ee31bf9c2ab195d66337d52e4a1bb7075ac76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="comparison-operators-in-visual-basic"></a>Operatory porównania w Visual Basic
Operatory porównania porównać dwa wyrażenia i zwraca `Boolean` wartość, która reprezentuje relację ich wartości. Brak operatorów porównywania wartości liczbowe, operatorów porównywania ciągów i operatorów porównywania obiektów. Wszystkie trzy typy operatorów omówiono poniżej.  
  
## <a name="comparing-numeric-values"></a>Porównanie wartości numerycznych  
 Visual Basic porównuje wartości liczbowych przy użyciu sześciu operatorów porównanie liczbowe. Każdy operator przyjmuje jako argumentów dwóch wyrażeń określających wartości liczbowych. Poniższa tabela zawiera listę operatory i przedstawiono przykłady każdego.  
  
|Operator|Warunek przetestowane|Przykłady|  
|--------------|----------------------|--------------|  
|`=` (Równości)|Jest to wartość pierwszego równości wyrażenia na wartość drugiego?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (Nierówności)|Wartość pierwsze wyrażenie jest nierówne na wartość drugiego?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (Poniżej)|Jest to wartość pierwsze wyrażenie mniejsza niż wartość drugiego?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (Więcej niż)|Wartość pierwsze wyrażenie jest większa niż wartość drugiego?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (Mniejsze niż lub równe)|Wartość pierwsze wyrażenie jest mniejsza niż wartość drugiego?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (Większe niż lub równe)|To jest wartość pierwsze wyrażenie większa lub równa wartości drugiego?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Porównywanie ciągów  
 Visual Basic porównuje ciągów za pomocą [operatora Like](../../../../visual-basic/language-reference/operators/like-operator.md) oraz operatorów porównanie liczbowe. `Like` Operator umożliwia określenie wzorca. Ten ciąg jest porównywane ze wzorcem i jeśli jest on zgodny, wynik jest `True`. W przeciwnym razie wynikiem jest `False`. Operatory liczbowe można porównywać `String` wartości w zależności od ich kolejność sortowania, jak przedstawiono na poniższym przykładzie.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 W rezultacie w poprzednim przykładzie `True` ponieważ pierwszy znak w ciągu pierwszego sortuje przed pierwszym znakiem w drugi ciąg. Jeśli pierwsze znaki były takie same, porównanie będzie w dalszym ciągu następny znak w obu ciągów i tak dalej. Może także przetestować porównania ciągów za pomocą operatora równości, jak przedstawiono na poniższym przykładzie.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Czy prefiksu innego, takie jak "aa" i "aaa", jest jeden ciąg dłuższy ciąg jest uznawane za większy niż krótszego ciągu. Ilustruje to poniższy przykład.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Kolejność sortowania opiera się na porównanie binarne lub porównanie tekstowe, w zależności od ustawienia `Option Compare`. Aby uzyskać więcej informacji, zobacz [instrukcji porównanie opcji](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Porównanie obiektów  
 Visual Basic porównuje dwie zmienne odwołań do obiektów z [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) i [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md). Aby ustalić, czy dwie zmienne odwołujące się odwoływać się do tego samego wystąpienia obiektu, można użyć jednej z tych operatorów. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 W powyższym przykładzie `x Is y` daje w wyniku `True`, ponieważ obie zmienne odwoływać się do tego samego wystąpienia. Natomiast wynik z następującym przykładzie.  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 W powyższym przykładzie `x Is y` daje w wyniku `False`, mimo że zmienne odwoływać się do obiektów tego samego typu, odwołuje się do innego wystąpienia tego typu.  
  
 Jeśli chcesz sprawdzić, czy dwa obiekty nie wskazuje na to samo wystąpienie `IsNot` operator pozwala uniknąć gramatycznie clumsy kombinację `Not` i `Is`. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 W powyższym przykładzie `If a IsNot b` jest odpowiednikiem `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Porównywanie typ obiektu  
 Można sprawdzić, czy obiekt jest określonego typu z `TypeOf`... `Is` wyrażenia. Składnia jest następująca:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Gdy `typename` Określa typ interfejsu, a następnie `TypeOf`... `Is` zwraca wyrażenie `True` Jeśli obiekt implementuje typu interfejsu. Gdy `typename` jest typ klasy, a następnie zwraca wyrażenie `True` Jeśli obiekt jest wystąpienie określonej klasy lub klasą pochodzącą z określonej klasy. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 W powyższym przykładzie `TypeOf x Is Control` wyrażenie daje w wyniku `True` ponieważ typ `x` jest `Button`, który dziedziczy z `Control`.  
  
 Aby uzyskać więcej informacji, zobacz [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Operatory](../../../../visual-basic/language-reference/operators/index.md)  
 [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operatory łączenia w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
