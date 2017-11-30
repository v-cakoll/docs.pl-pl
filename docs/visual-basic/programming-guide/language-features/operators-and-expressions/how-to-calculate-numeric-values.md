---
title: "Porady: obliczanie wartości liczbowych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Porady: obliczanie wartości liczbowych (Visual Basic)
Można obliczyć wartości liczbowych za pomocą wyrażeń liczbowych. A *wyrażenia liczbowego* jest wyrażenie, które zawiera literały, stałe i zmienne reprezentujący wartości liczbowych i operatory, które działają na tych wartości.  
  
## <a name="calculating-numeric-values"></a>Obliczanie wartości liczbowych  
  
#### <a name="to-calculate-a-numeric-value"></a>Obliczanie wartości liczbowych  
  
-   Łączenie co najmniej jeden literały numeryczne, stałe i zmienne w wyrażenia liczbowego. W poniższym przykładzie przedstawiono niektóre prawidłowe wyrażenia liczbowego.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     Pierwsze trzy wiersze zawierają literałem stałej i zmiennej. Każda z nich stanowi prawidłowe wyrażenie liczbowe samodzielnie. Końcowe wiersz zawiera kombinację zmiennej z dwóch literały.  
  
     Należy pamiętać, że wyrażenie liczbowe nie tworzą pełnego [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instrukcji samodzielnie. Należy użyć wyrażenia jako część pełną instrukcję.  
  
#### <a name="to-store-a-numeric-value"></a>Do przechowywania wartości numerycznej  
  
-   Aby przypisać wartość reprezentowanego przez wyrażenie liczbowe do zmiennej, jak w poniższym przykładzie pokazano służy instrukcji przypisania.  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     W powyższym przykładzie wartość wyrażenie po prawej stronie operatora równa (`=`) jest przypisany do zmiennej `j` po lewej stronie operatora, więc `j` daje w wyniku 276.  
  
     Aby uzyskać więcej informacji, zobacz [instrukcje](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Wiele operatorów  
 Jeśli wyrażenie liczbowe zawiera więcej niż jeden operator, kolejność, w jakiej są oceniane jest określana przez reguły pierwszeństwo operatorów. Aby zastąpić reguły pierwszeństwa operatora, ujmij wyrażenia w nawiasach, tak jak w powyższym przykładzie; zamknięte wyrażenia są sprawdzane jako pierwsze.  
  
#### <a name="to-override-normal-operator-precedence"></a>Aby zastąpić normalne kolejność wykonywania działań  
  
-   Umieść nawiasy operacje, które można wykonać pierwsze. W poniższym przykładzie pokazano dwa różne wyniki z tej samej argumenty i operatory.  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     W powyższym przykładzie obliczeń dla `j` wykonuje operator dodawania (`+`) pierwszego ponieważ nawiasy, `(67 + i)` zastąpienia normalnym priorytecie, a wartość przypisana do `j` jest 276 (4 razy 69). Obliczanie dla `k` wykonuje operatorów w ich normalnym pierwszeństwa (`*` przed `+`) i wartość przypisana do `k` jest 270 (268 plus 2).  
  
     Aby uzyskać więcej informacji, zobacz [kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory arytmetyczne](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
