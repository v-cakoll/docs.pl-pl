---
title: 'Porady: obliczanie wartości liczbowych'
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
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348970"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Porady: obliczanie wartości liczbowych (Visual Basic)
Wartości liczbowe można obliczyć przy użyciu wyrażeń liczbowych. *Wyrażenie liczbowe* jest wyrażeniem zawierającym literały, stałe i zmienne reprezentujące wartości liczbowe oraz operatory, które działają na tych wartościach.  
  
## <a name="calculating-numeric-values"></a>Obliczanie wartości liczbowych  
  
#### <a name="to-calculate-a-numeric-value"></a>Aby obliczyć wartość liczbową  
  
- Połącz jeden lub więcej literałów liczbowych, stałych i zmiennych w wyrażenie liczbowe. Poniższy przykład pokazuje nieprawidłowe wyrażenia liczbowe.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     Pierwsze trzy wiersze przedstawiają literał, stałą i zmienną. Każdy z nich tworzy prawidłowe wyrażenie liczbowe. Ostatni wiersz zawiera kombinację zmiennej z dwoma literałami.  
  
     Należy zauważyć, że wyrażenie liczbowe nie tworzy kompletnej instrukcji Visual Basic. Należy użyć wyrażenia jako części kompletnej instrukcji.  
  
#### <a name="to-store-a-numeric-value"></a>Aby zapisać wartość liczbową  
  
- Można użyć instrukcji przypisania, aby przypisać wartość reprezentowaną przez wyrażenie liczbowe do zmiennej, jak pokazano w poniższym przykładzie.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     W powyższym przykładzie wartość wyrażenia po prawej stronie operatora równości (`=`) jest przypisana do zmiennej `j` po lewej stronie operatora, dlatego `j` oblicza do 276.  
  
     Aby uzyskać więcej informacji, zobacz [instrukcje](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Wiele operatorów  
 Jeśli wyrażenie liczbowe zawiera więcej niż jeden operator, kolejność, w której są oceniane, zależy od reguł pierwszeństwa operatora. Aby zastąpić reguły pierwszeństwa operatorów, należy umieścić wyrażenia w nawiasach, jak w powyższym przykładzie. ujęte wyrażenia są oceniane jako pierwsze.  
  
#### <a name="to-override-normal-operator-precedence"></a>Aby zastąpić normalne pierwszeństwo operatorów  
  
- Użyj nawiasów, aby ująć operacje, które mają zostać wykonane jako pierwsze. Poniższy przykład przedstawia dwa różne wyniki z tymi samymi operandami i operatorami.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     W poprzednim przykładzie, obliczenie dla `j` wykonuje najpierw operator dodawania (`+`), ponieważ nawiasy wokół `(67 + i)` przesłaniają normalne pierwszeństwo, a wartość przypisana do `j` to 276 (4 razy 69). Obliczenie dla `k` wykonuje operatory w ich normalnym pierwszeństwie (`*` przed `+`), a wartość przypisana do `k` to 270 (268 plus 2).  
  
     Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz także

- [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory arytmetyczne](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
