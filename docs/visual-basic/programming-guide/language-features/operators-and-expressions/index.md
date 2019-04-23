---
title: Operatory i wyrażenia w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: b762c3002913cbd925579ef28f2aa01411976c32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073653"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Operatory i wyrażenia w Visual Basic
*Operator* jest element kodu, który wykonuje operację na elementy kodu, które zawierają wartości. Elementy wartości obejmują zmienne, stałe, literały, właściwości, zwraca z `Function` i `Operator` procedur i wyrażeń.  
  
 *Wyrażenie* jest serią wartości elementów w połączeniu z operatorami, która daje w wyniku nową wartość. Operatory działają w przypadku elementów wartość, wykonując obliczenia, porównania lub innych operacji.  
  
## <a name="types-of-operators"></a>Typy operatorów  
 Visual Basic oferuje następujące operatory:  
  
-   [Operatory arytmetyczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) wykonywanie obliczeń dobrze znanych na wartości liczbowe, łącznie z ich wzorców bitowe przesunięcie.  
  
-   [Operatory porównania](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porównać dwa wyrażenia i zwraca `Boolean` wartość reprezentująca wynik porównania.  
  
-   [Concatenation — operatory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) Dołącz do wielu ciągów w jeden ciąg.  
  
-   [Logiczne i bitowe operatory w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) połączyć `Boolean` lub wartości liczbowych i zwracają wynik o ten sam typ danych jako wartości.  
  
 Elementy wartości, które są połączone z operatorem są nazywane *operandy* tego operatora. Operatory w połączeniu z wyrażenia formularza elementów wartości, z wyjątkiem operatora przypisania, który stanowi *instrukcji*. Aby uzyskać więcej informacji, zobacz [instrukcji](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>Obliczanie wyrażeń  
 Wynik końcowy wyrażenie reprezentuje wartość, która jest zazwyczaj dobrze znanych danych typu, takich jak `Boolean`, `String`, lub typu liczbowego.  
  
 Poniżej przedstawiono przykłady wyrażeń.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Wiele operatorów może wykonywać akcje w pojedyncze wyrażenie lub instrukcję, tak jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 W powyższym przykładzie Visual Basic wykonuje operacje w wyrażeniu po prawej stronie operatora przypisania (`=`), następnie przypisuje wynikowej wartości do zmiennej `x` po lewej stronie. Nie ma żadnego limitu praktyczne liczby operatorów, które mogą być połączone w wyrażeniu, ale zrozumienie [pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) jest niezbędne do zapewnienia, że otrzymujesz oczekiwanych wyników.  

## <a name="see-also"></a>Zobacz także

- [Operatory](../../../../visual-basic/language-reference/operators/index.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)
