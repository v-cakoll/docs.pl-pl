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
ms.openlocfilehash: 8d34eb4c8b14bb4754f2a3cf5b6f9a7601aa4662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388961"
---
# <a name="boolean-expressions-visual-basic"></a>Wyrażenia logiczne (Visual Basic)
*Wyrażenie logiczne* jest wyrażeniem, którego wynikiem jest wartość [typu danych Boolean](../../../language-reference/data-types/boolean-data-type.md): `True` lub `False` . `Boolean`wyrażenia mogą mieć kilka form. Najprostszym jest bezpośrednie porównanie wartości `Boolean` zmiennej z `Boolean` literałem, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>Dwie orednie operatora =  
 Zwróć uwagę, że instrukcja przypisania `newCustomer = True` wygląda tak samo jak wyrażenie w poprzednim przykładzie, ale wykonuje inną funkcję i jest używana inaczej. W poprzednim przykładzie wyrażenie `newCustomer = True` reprezentuje wartość logiczną, a `=` znak jest interpretowany jako operator porównania. W instrukcji autonomicznej `=` znak jest interpretowany jako operator przypisania i przypisuje wartość po prawej stronie do zmiennej po lewej stronie. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Aby uzyskać więcej informacji, zobacz [porównania wartości](value-comparisons.md) i [instrukcje](../../../language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operatory porównania  
 Operatory porównania, takie jak `=` ,,,, `<` `>` `<>` `<=` i `>=` generują wyrażenia logiczne, porównując wyrażenie po lewej stronie operatora z wyrażeniem po prawej stronie operatora i oceniając wynik jako `True` lub `False` . Ilustruje to poniższy przykład.  
  
 `42 < 81`  
  
 Ponieważ 42 jest mniejsza niż 81, wyrażenie logiczne w powyższym przykładzie oblicza wartość `True` . Aby uzyskać więcej informacji na temat tego rodzaju wyrażenia, zobacz [porównania wartości](value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operatory porównania połączone z operatorami logicznymi  
 Wyrażenia porównania można łączyć za pomocą operatorów logicznych w celu tworzenia bardziej złożonych wyrażeń logicznych. Poniższy przykład demonstruje użycie operatorów porównania w połączeniu z operatorem logicznym.  
  
 `x > y And x < 1000`  
  
 W powyższym przykładzie wartość wyrażenia ogólnego zależy od wartości wyrażeń po każdej stronie `And` operatora. Jeśli oba wyrażenia są `True` , wyrażenie ogólne oblicza wartość `True` . Jeśli jedno z wyrażeń ma wartość `False` , całe wyrażenie zwróci wartość `False` .  
  
## <a name="short-circuiting-operators"></a>Operatory krótkiego obwodu  
 Operatory logiczne `AndAlso` i `OrElse` wykazują zachowanie znane jako *krótkie obwody*. Operator skracania obwodu najpierw oblicza pierwszy operand. Jeśli argument operacji po lewej stronie określa wartość całego wyrażenia, wykonanie programu jest realizowane bez oceniania prawego wyrażenia. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 W poprzednim przykładzie operator oblicza lewe wyrażenie, `45 < 12` . Ponieważ lewe wyrażenie zwraca wartość `False` , całe wyrażenie logiczne musi być szacowane do `False` . Wykonanie programu w ten sposób pomija wykonywanie kodu w `If` bloku bez oceniania prawego wyrażenia `testFunction(3)` . W tym przykładzie nie jest wywoływana `testFunction()` , ponieważ lewe wyrażenie powoduje sfałszowanie całego wyrażenia.  
  
 Podobnie, jeśli lewe wyrażenie w wyrażeniu logicznym używającym `OrElse` wartości oblicza do `True` , wykonanie przechodzi do następnego wiersza kodu bez szacowania prawego wyrażenia, ponieważ wyrażenie po lewej stronie ma już zweryfikowane całe wyrażenie.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Porównanie z operatorami niebędącymi niewielkim obwodem  
 Z kolei obie strony operatora logicznego są oceniane, gdy operatory logiczne `And` i `Or` są używane. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 Powyższy przykład wywołuje, chociaż `testFunction()` wyrażenie Left zwraca wartość `False` .  
  
## <a name="parenthetical-expressions"></a>Wyrażenia w nawiasach  
 Można użyć nawiasów do kontrolowania kolejności oceny wyrażeń logicznych. Wyrażenia ujęte w nawiasy są oceniane jako pierwsze. W przypadku wielu poziomów zagnieżdżenia pierwszeństwo jest przyznawane do najbardziej głęboko zagnieżdżonych wyrażeń. W nawiasach oceny są przeprowadzane zgodnie z regułami pierwszeństwa operatorów. Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w Visual Basic](../../../language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz też

- [Operatory logiczne i bitowe w Visual Basic](logical-and-bitwise-operators.md)
- [Porównania wartości](value-comparisons.md)
- [Instrukcje](../statements.md)
- [Operatory porównania](../../../language-reference/operators/comparison-operators.md)
- [Skuteczna kombinacja operatorów](efficient-combination-of-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](../../../language-reference/operators/operator-precedence.md)
- [Boolean, typ danych](../../../language-reference/data-types/boolean-data-type.md)
