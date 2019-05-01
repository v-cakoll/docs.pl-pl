---
title: 'Instrukcje: Obliczanie wartości liczbowych (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 33184d9be275f5e777ffd79c6dd4e3182d865de7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864685"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Instrukcje: Obliczanie wartości liczbowych (Visual Basic)
Można obliczyć wartości liczbowych za pomocą wyrażeń liczbowych. A *wyrażenia liczbowego* to wyrażenie, które zawiera literały, stałe i zmienne reprezentujące wartości liczbowe i operatory, które działają w tych wartości.  
  
## <a name="calculating-numeric-values"></a>Obliczanie wartości liczbowych  
  
#### <a name="to-calculate-a-numeric-value"></a>Obliczanie wartości liczbowych  
  
- Połącz co najmniej jeden literały numeryczne, stałe i zmienne w wyrażenia liczbowego. Poniższy przykład pokazuje niektóre prawidłowe wyrażenia liczbowego.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     Pierwsze trzy wiersze Pokaż literałem stałej i zmiennej. Każdy z nich stanowi prawidłowe wyrażenie liczbowe samodzielnie. Ostatni wiersz zawiera kombinację zmiennego dwa literały.  
  
     Należy pamiętać, że wyrażenie liczbowe nie tworzą pełną instrukcję języka Visual Basic samodzielnie. Należy użyć wyrażenia jako część pełną instrukcję.  
  
#### <a name="to-store-a-numeric-value"></a>Do przechowywania wartości liczbowych  
  
- Aby przypisać wartość reprezentowane przez wyrażenie liczbowe do zmiennej, tak jak pokazano w poniższym przykładzie, można użyć instrukcji przypisania.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     W poprzednim przykładzie wartość wyrażenia po prawej stronie operatora równa (`=`) jest przypisany do zmiennej `j` po lewej stronie operatora, dzięki czemu `j` daje w wyniku 276.  
  
     Aby uzyskać więcej informacji, zobacz [instrukcji](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Wiele operatorów  
 Jeśli wyrażenie liczbowe zawiera więcej niż jeden operator, kolejność, w jakiej są oceniane jest określana przez reguły pierwszeństwa operatorów. Aby zastąpić reguły pierwszeństwa operatorów, ujmij wyrażeń w nawiasach, tak jak w powyższym przykładzie; ujęty wyrażenia są obliczane jako pierwsze.  
  
#### <a name="to-override-normal-operator-precedence"></a>Do zastępowania normalnego kolejność wykonywania działań  
  
- Użyj nawiasów, aby ująć operacje, które mają zostać wykonane jako pierwsze. Poniższy przykład przedstawia dwa różne wyniki przy użyciu tych samych argumentów i operatorów.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     W powyższym przykładzie obliczeń dla `j` wykonuje operator dodawania (`+`) pierwszego ponieważ nawiasów wokół `(67 + i)` zastępują normalny priorytet i wartość przypisana do `j` jest 276 (4 razy 69). Obliczeń dla `k` wykonuje operatorów w ich normalnym priorytecie (`*` przed `+`), a wartość przypisana do `k` jest 270 (268 plus 2).  
  
     Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz także

- [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory arytmetyczne](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
