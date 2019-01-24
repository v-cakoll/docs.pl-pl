---
title: Wyrażenia logiczne (Visual Basic)
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
ms.openlocfilehash: a86df2734d315e5fed0784b0394bb305b15562a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562755"
---
# <a name="boolean-expressions-visual-basic"></a>Wyrażenia logiczne (Visual Basic)
A *wyrażenia logicznego* jest wyrażeniem, którego wynikiem jest wartość [typ danych Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` lub `False`. `Boolean` wyrażenia może przybierać różne formy. Najprostszą jest bezpośrednie porównanie wartości `Boolean` zmienną `Boolean` literału, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>Dwa znaczenie = — Operator  
 Należy zauważyć, że instrukcja przypisania `newCustomer = True` wygląda tak samo jak w wyrażeniu w poprzednim przykładzie, ale wykonuje różne funkcje i jest używane w inny sposób. W powyższym przykładzie wyrażenie `newCustomer = True` reprezentuje wartość logiczną, a `=` znaku jest interpretowany jako operator porównania. W instrukcji autonomicznej `=` znaku jest interpretowany jako operator przypisania i przypisuje wartość po prawej stronie do zmiennej po lewej stronie. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) i [instrukcji](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operatory porównania  
 Operatory porównania, takie jak `=`, `<`, `>`, `<>`, `<=`, i `>=` tworzyć wyrażenia logiczne, porównując wyrażenie po lewej stronie operatora wyrażenie po prawej stronie operator i ocenianie wynik w postaci `True` lub `False`. Ilustruje to poniższy przykład.  
  
 `42 < 81`  
  
 Ponieważ 42 jest mniejsza niż 81, wyrażenia logicznego w poprzednim przykładzie daje w wyniku `True`. Aby uzyskać więcej informacji na temat tego rodzaju wyrażeń, zobacz [porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operatory porównania w połączeniu z operatorami logicznymi  
 Wyrażeniach porównania mogą być połączone za pomocą operatorów logicznych w celu utworzenia bardziej złożonych wyrażeń logicznych. Poniższy przykład demonstruje użycie operatorów porównania w połączeniu z operatorem logicznym.  
  
 `x > y And x < 1000`  
  
 W poprzednim przykładzie wartość wyrażenia zależy od wartości wyrażenia na każdej stronie `And` operatora. Jeśli oba wyrażenia są `True`, wówczas daje w wyniku wyrażenia `True`. Jeśli jedno z tych wyrażeń `False`, a następnie całe wyrażenie daje w wyniku `False`.  
  
## <a name="short-circuiting-operators"></a>Zwarcie operatorów  
 Operatory logiczne `AndAlso` i `OrElse` wykazują zachowanie nazywane *zwarcie*. Short-circuiting operator najpierw sprawdza lewy operand. Jeśli lewy operand określa wartość całe wyrażenie, wykonywania programu będzie kontynuowane bez oceny wyrażenie prawej krawędzi. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 W powyższym przykładzie operator oblicza wyrażenie po lewej stronie, `45 < 12`. Ponieważ lewe wyrażenie daje w wyniku `False`, całe wyrażenie logiczne musi być `False`. Wykonanie programu więc pomija wykonywanie kodu w ramach `If` bloku bez oceny prawe wyrażenie `testFunction(3)`. W tym przykładzie nie mogą wywoływać `testFunction()` ponieważ po lewej stronie wyrażenia falsifies całe wyrażenie.  
  
 Podobnie jeśli wyrażenie po lewej stronie wyrażenia logicznego przy użyciu `OrElse` daje w wyniku `True`, wykonanie przechodzi do następnego wiersza kodu bez oceny prawe wyrażenie, ponieważ wyrażenie po lewej stronie został już zweryfikowany całą wyrażenie.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Porównanie z operatorami Circuiting krótki  
 Z drugiej strony, obie strony operatora logicznego są oceniane po operatorów logicznych `And` i `Or` są używane. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 Poprzedni przykład wywołuje `testFunction()` nawet, jeśli wynikiem obliczenia wyrażenia po lewej stronie jest `False`.  
  
## <a name="parenthetical-expressions"></a>Wyrażenia w nawiasach  
 Można użyć nawiasów, można określić kolejność obliczania wyrażeń logicznych. Najpierw należy ocenić wyrażenia ujętego w nawiasy. Wiele poziomów zagnieżdżenia przyznano pierwszeństwo najgłębiej zagnieżdżoną wyrażenia. Wewnątrz nawiasów ocena będzie kontynuowana zgodnie z regułami pierwszeństwo operatorów. Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz także
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instrukcje](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Boolean, typ danych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
