---
title: Wyrażenia logiczne
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 1000ec6e4b35d0cb2c6232b50f9a9551cb0dfdcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350809"
---
# <a name="boolean-expressions-visual-basic"></a>Wyrażenia logiczne (Visual Basic)
*Wyrażenie logiczne* jest wyrażeniem, którego wynikiem jest wartość [typu danych Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` lub `False`. wyrażenia `Boolean` mogą mieć kilka form. Najprostszym jest bezpośrednie porównanie wartości zmiennej `Boolean` z `Boolean` literal, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>Dwie orednie operatora =  
 Zwróć uwagę, że instrukcja przypisania `newCustomer = True` wygląda tak samo jak wyrażenie w poprzednim przykładzie, ale wykonuje inną funkcję i jest używana inaczej. W poprzednim przykładzie wyrażenie `newCustomer = True` reprezentuje wartość logiczną, a znak `=` jest interpretowany jako operator porównania. W instrukcji autonomicznej znak `=` jest interpretowany jako operator przypisania i przypisuje wartość po prawej stronie do zmiennej po lewej stronie. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Aby uzyskać więcej informacji, zobacz [porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) i [instrukcje](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operatory porównania  
 Operatory porównania, takie jak `=`, `<`, `>`, `<>`, `<=`i `>=` generują wyrażenia logiczne, porównując wyrażenie po lewej stronie operatora z wyrażeniem po prawej stronie operatora i oceniając wynik jako `True` lub `False`. Ilustruje to poniższy przykład.  
  
 `42 < 81`  
  
 Ponieważ 42 jest mniejsza niż 81, wyrażenie logiczne w powyższym przykładzie oblicza wartość `True`. Aby uzyskać więcej informacji na temat tego rodzaju wyrażenia, zobacz [porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operatory porównania połączone z operatorami logicznymi  
 Wyrażenia porównania można łączyć za pomocą operatorów logicznych w celu tworzenia bardziej złożonych wyrażeń logicznych. Poniższy przykład demonstruje użycie operatorów porównania w połączeniu z operatorem logicznym.  
  
 `x > y And x < 1000`  
  
 W powyższym przykładzie wartość wyrażenia ogólnego zależy od wartości wyrażeń po każdej stronie operatora `And`. Jeśli oba wyrażenia są `True`, wyrażenie ogólne oblicza `True`. Jeśli jedno z wyrażeń jest `False`, całe wyrażenie szacuje się na `False`.  
  
## <a name="short-circuiting-operators"></a>Operatory krótkiego obwodu  
 Operatory logiczne `AndAlso` i `OrElse` wykazują zachowanie znane jako *krótkie obwody*. Operator skracania obwodu najpierw oblicza pierwszy operand. Jeśli argument operacji po lewej stronie określa wartość całego wyrażenia, wykonanie programu jest realizowane bez oceniania prawego wyrażenia. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 W poprzednim przykładzie operator oblicza wyrażenie Left, `45 < 12`. Ponieważ lewe wyrażenie szacuje się `False`, całe wyrażenie logiczne musi być szacowane, aby `False`. Wykonanie programu w ten sposób pomija wykonywanie kodu w bloku `If` bez oceniania prawego wyrażenia, `testFunction(3)`. Ten przykład nie wywołuje `testFunction()`, ponieważ lewe wyrażenie powoduje sfałszowanie całego wyrażenia.  
  
 Podobnie, jeśli lewe wyrażenie w wyrażeniu logicznym wykorzystujące `OrElse` oblicza do `True`, wykonywanie przechodzi do następnego wiersza kodu bez oceniania prawego wyrażenia, ponieważ lewe wyrażenie ma już zweryfikowane całe wyrażenie.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Porównanie z operatorami niebędącymi niewielkim obwodem  
 Z kolei obie strony operatora logicznego są oceniane, gdy operatory logiczne `And` i `Or` są używane. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 Powyższy przykład wywołuje `testFunction()`, chociaż wyrażenie Left zwraca `False`.  
  
## <a name="parenthetical-expressions"></a>Wyrażenia w nawiasach  
 Można użyć nawiasów do kontrolowania kolejności oceny wyrażeń logicznych. Wyrażenia ujęte w nawiasy są oceniane jako pierwsze. W przypadku wielu poziomów zagnieżdżenia pierwszeństwo jest przyznawane do najbardziej głęboko zagnieżdżonych wyrażeń. W nawiasach oceny są przeprowadzane zgodnie z regułami pierwszeństwa operatorów. Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instrukcje](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Boolean, typ danych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
