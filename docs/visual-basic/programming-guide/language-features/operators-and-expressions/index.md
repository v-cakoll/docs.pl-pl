---
title: Operatory i wyrażenia
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
ms.openlocfilehash: dcf52c6200193f81070f323c8037ad82d747942d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403436"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Operatory i wyrażenia w Visual Basic
*Operator* jest elementem kodu, który wykonuje operację na jednym lub większej liczbie elementów kodu, które przechowują wartości. Elementy wartości to zmienne, stałe, literały, właściwości, zwracane z `Function` i `Operator` procedury i wyrażenia.  
  
 *Wyrażenie* jest serią elementów wartości połączonych z operatorami, które dają nową wartość. Operatory działają na elementach wartości przez wykonywanie obliczeń, porównań lub innych operacji.  
  
## <a name="types-of-operators"></a>Typy operatorów  
 Visual Basic udostępnia następujące typy operatorów:  
  
- [Operatory arytmetyczne](arithmetic-operators.md) wykonują znane obliczenia na wartościach liczbowych, w tym przesunięcie ich wzorców bitowych.  
  
- [Operatory porównania](comparison-operators.md) porównują dwa wyrażenia i zwracają `Boolean` wartość reprezentującą wynik porównania.  
  
- [Operatory łączenia](concatenation-operators.md) sprzęga wiele ciągów w jeden ciąg.  
  
- [Operatory logiczne i bitowe w Visual Basic](logical-and-bitwise-operators.md) łączenia `Boolean` lub wartości liczbowych i zwracają wynik tego samego typu danych co wartości.  
  
 Elementy wartości, które są połączone z operatorem, są nazywane *operandami* tego operatora. Operatory połączone z wyrażeniami elementów wartości, z wyjątkiem operatora przypisania, który tworzy *instrukcję*. Aby uzyskać więcej informacji, zobacz [instrukcje](../statements.md).  
  
## <a name="evaluation-of-expressions"></a>Obliczanie wyrażeń  
 Wynik końcowy wyrażenia reprezentuje wartość, która jest zazwyczaj znanym typem danych, takim jak `Boolean` , `String` lub typu liczbowego.  
  
 Poniżej przedstawiono przykłady wyrażeń.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Kilka operatorów może wykonywać akcje w pojedynczym wyrażeniu lub instrukcji, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 W poprzednim przykładzie Visual Basic wykonuje operacje w wyrażeniu po prawej stronie operatora przypisania ( `=` ), a następnie przypisuje wartość wyniki do zmiennej `x` po lewej. Nie ma praktycznego limitu liczby operatorów, które mogą być połączone w wyrażeniu, ale w celu uzyskania oczekiwanych wyników należy zrozumieć [pierwszeństwo operatorów w Visual Basic](../../../language-reference/operators/operator-precedence.md) .  

## <a name="see-also"></a>Zobacz też

- [Operatory](../../../language-reference/operators/index.md)
- [Skuteczna kombinacja operatorów](efficient-combination-of-operators.md)
- [Instrukcje](../../../language-reference/statements/index.md)
