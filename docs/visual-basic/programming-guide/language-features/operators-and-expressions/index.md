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
ms.openlocfilehash: a0f6d026714f8e933dc75dbb7c3a5e6e8e1bd795
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805451"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Operatory i wyrażenia w Visual Basic
*Operator* jest element kodu, który wykonuje operacje na elementy kodu, które zawierają wartości. Wartość elementów obejmują zmienne, stałe, literały, właściwości, zwraca z `Function` i `Operator` procedur i wyrażenia.  
  
 *Wyrażenie* jest szereg elementów wartość w połączeniu z operatorami, która daje w wyniku nową wartość. Operatory działa w przypadku elementów wartość wykonując obliczenia, porównania lub innych operacji.  
  
## <a name="types-of-operators"></a>Typy operatorów  
 Visual Basic zapewnia następujące operatory:  
  
-   [Operatory arytmetyczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) obliczeń znanych na wartości liczbowe, łącznie z ich wzorców bitowe przesunięcie.  
  
-   [Operatory porównania](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porównać dwa wyrażenia i zwraca `Boolean` wartość reprezentująca wynik porównania.  
  
-   [Operatory łączenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) dołączyć wielu ciągów w jednym ciągu.  
  
-   [Logiczne i bitowe operatory w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) połączyć `Boolean` lub alfanumeryczne wartości i zwraca wynik tego samego typu danych jako wartości.  
  
 Elementy wartości, które są łączone za pomocą operatora są nazywane *operandy* tego operatora. Operatory w połączeniu z wartości wyrażenia formularza elementów, z wyjątkiem operatora przypisania który stanowi *instrukcji*. Aby uzyskać więcej informacji, zobacz [instrukcje](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>Obliczanie wyrażenia  
 W rezultacie wyrażenie reprezentuje wartość, która jest zazwyczaj znanych danych typu, takich jak `Boolean`, `String`, lub typ liczbowy.  
  
 Poniżej przedstawiono przykłady wyrażeń.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Wiele operatorów dostępne akcje w jedno wyrażenie lub instrukcję, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 W powyższym przykładzie Visual Basic wykonuje operacje w wyrażeniu po prawej stronie operatora przypisania (`=`), następnie przypisuje wynikowej wartości do zmiennej `x` po lewej stronie. Nie ma żadnego limitu praktyczne liczby operatory, które mogą być połączone w wyrażeniu, ale zrozumienia [kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) jest niezbędne mieć pewność, że wyniki spodziewasz się.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [przeciążanie operatora w Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory](../../../../visual-basic/language-reference/operators/index.md)  
 [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)
