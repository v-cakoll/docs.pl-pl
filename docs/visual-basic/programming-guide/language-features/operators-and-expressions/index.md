---
title: Operatory i wyrażenia w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7c32ce34dc7d6cb662ebdb42a3d3431f8107687f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [przeciążanie operatora w Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory](../../../../visual-basic/language-reference/operators/index.md)  
 [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)
