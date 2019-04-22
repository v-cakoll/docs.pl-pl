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
ms.openlocfilehash: d08974a929a723d4037300f9d72ae03c072d47fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826161"
---
# <a name="comparison-operators-in-visual-basic"></a>Operatory porównania w Visual Basic
Operatory porównania porównać dwa wyrażenia i zwraca `Boolean` wartość, która reprezentuje relację ich wartości. Brak operatory porównywania wartości liczbowych, operatory porównywania ciągów i operatory porównywania obiektów. Wszystkie trzy typy operatorów zostały omówione w niniejszym dokumencie.  
  
## <a name="comparing-numeric-values"></a>Porównanie wartości numerycznych  
 Visual Basic porównuje wartości liczbowych przy użyciu sześciu operatory porównanie numeryczne. Każdy operator przyjmuje jako argumenty operacji dwóch wyrażeń, które obliczają do wartości liczbowych. Poniższej tabeli wymieniono operatory i przedstawiono przykłady każdego z nich.  
  
|Operator|Testowany warunek|Przykłady|  
|--------------|----------------------|--------------|  
|`=` (Równości)|Wartość pierwszego równe wyrażenia jest wartość drugiego?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (Nierówność)|Wartość pierwsze wyrażenie jest nierówne wartość drugiego?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (Mniejsze niż)|Czy wartość pierwszego wyrażenia mniejszej niż wartość drugiego?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (Większe niż)|Wartość pierwsze wyrażenie jest większa niż wartość drugiego?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (Mniejsze niż lub równe)|Wartość pierwsze wyrażenie jest mniejsza niż wartość drugiego?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (Większe niż lub równe)|Jest wartością pierwsze wyrażenie, większa lub równa wartości drugiego?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Porównywanie ciągów  
 Visual Basic porównuje ciągi przy użyciu [takich jak Operator](../../../../visual-basic/language-reference/operators/like-operator.md) oraz operatory porównanie numeryczne. `Like` Operator służy do określania wzorca. Ten ciąg jest porównywane ze wzorca, a jeśli jest zgodny, wynik jest `True`. W przeciwnym razie wynikiem jest `False`. Operatory numeryczne umożliwia porównanie `String` wartości oparte na ich kolejność sortowania, co ilustruje poniższy przykład.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 W wyniku w poprzednim przykładzie `True` ponieważ pierwszy znak w ciągu pierwszego sortowaniu znajduje się przed pierwszego znaku w ciągu drugiego. Pierwsze znaki były równe, porównanie będzie w dalszym ciągu następnego znaku w obu ciągów i tak dalej. Możesz także testować porównania ciągów za pomocą operatora równości, co ilustruje poniższy przykład.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Jeśli jeden ciąg prefiksu innego, takie jak "aa" i "aaa" dłuższy ciąg jest uważana za większy niż krótszego ciągu. Ilustruje to poniższy przykład.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Kolejność sortowania jest oparty na porównanie binarne lub porównanie tekstowe, w zależności od ustawień `Option Compare`. Aby uzyskać więcej informacji, zobacz [instrukcji porównanie opcji](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Porównywanie obiektów  
 Visual Basic porównuje dwie zmienne odwołań do obiektów z [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) i [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md). Aby ustalić, czy dwie zmienne odwołujące się odwoływać się do tego samego wystąpienia obiektu, można użyć jednej z tych operatorów. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 W powyższym przykładzie `x Is y` daje w wyniku `True`, ponieważ obie zmienne odnoszą się do tego samego wystąpienia. Porównaj wynik z poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 W powyższym przykładzie `x Is y` daje w wyniku `False`, ponieważ mimo że zmienne odnoszą się do obiektów tego samego typu, odnoszą się do innego wystąpienia tego typu.  
  
 Jeśli chcesz sprawdzić, czy dwa obiekty nie wskazuje na to samo wystąpienie `IsNot` operator pozwala uniknąć gramatycznie clumsy kombinacją `Not` i `Is`. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 W powyższym przykładzie `If a IsNot b` jest odpowiednikiem `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Porównanie typ obiektu  
 Możesz sprawdzić, czy obiekt jest określonego typu z `TypeOf`... `Is` wyrażenia. Składnia jest następująca:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Gdy `typename` Określa typ interfejsu, a następnie `TypeOf`... `Is` zwraca wyrażenie `True` Jeśli obiekt implementuje typ interfejsu. Gdy `typename` jest typu klasy, a następnie zwraca wyrażenie `True` Jeśli obiekt jest wystąpieniem określonej klasy lub klasy, która dziedziczy po określonej klasy. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 W powyższym przykładzie `TypeOf x Is Control` wyrażenie daje w wyniku `True` ponieważ typ `x` jest `Button`, który dziedziczy z `Control`.  
  
 Aby uzyskać więcej informacji, zobacz [TypeOf — Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Zobacz także

- [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operatory](../../../../visual-basic/language-reference/operators/index.md)
- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory łączenia w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
