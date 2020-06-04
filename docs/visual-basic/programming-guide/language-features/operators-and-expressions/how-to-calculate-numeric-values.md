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
ms.openlocfilehash: 94b02693f308dcfcfa6983f2750a26d9d419f7be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403462"
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
  
     W powyższym przykładzie wartość wyrażenia po prawej stronie operatora równości ( `=` ) jest przypisywana do zmiennej `j` po lewej stronie operatora, a więc jest `j` równa 276.  
  
     Aby uzyskać więcej informacji, zobacz [instrukcje](../../../language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Wiele operatorów  
 Jeśli wyrażenie liczbowe zawiera więcej niż jeden operator, kolejność, w której są oceniane, zależy od reguł pierwszeństwa operatora. Aby zastąpić reguły pierwszeństwa operatorów, należy umieścić wyrażenia w nawiasach, jak w powyższym przykładzie. ujęte wyrażenia są oceniane jako pierwsze.  
  
#### <a name="to-override-normal-operator-precedence"></a>Aby zastąpić normalne pierwszeństwo operatorów  
  
- Użyj nawiasów, aby ująć operacje, które mają zostać wykonane jako pierwsze. Poniższy przykład przedstawia dwa różne wyniki z tymi samymi operandami i operatorami.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     W poprzednim przykładzie, obliczenie dla `j` wykonuje operator dodawania ( `+` ), ponieważ nawiasy wokół `(67 + i)` normalnych pierwszeństwa zastępują, a wartość przypisana do `j` jest 276 (4 razy 69). Obliczenie dla `k` wykonuje operatory w ich normalnym pierwszeństwie ( `*` przed `+` ) i wartość przypisaną do `k` 270 (268 plus 2).  
  
     Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w Visual Basic](../../../language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Zobacz też

- [Operatory i wyrażenia](index.md)
- [Porównania wartości](value-comparisons.md)
- [Instrukcje](../../../language-reference/statements/index.md)
- [Kolejność wykonywania działań (Visual Basic)](../../../language-reference/operators/operator-precedence.md)
- [Operatory arytmetyczne](../../../language-reference/operators/arithmetic-operators.md)
- [Skuteczna kombinacja operatorów](efficient-combination-of-operators.md)
