---
title: Not, operator
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 56cdeb80a217dbce15921eddd6a43d8d1b049376
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401462"
---
# <a name="not-operator-visual-basic"></a>Not — Operator (Visual Basic)
Wykonuje logiczne negację `Boolean` wyrażenia lub bitową negację wyrażenia liczbowego.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. `Boolean`Wyrażenie dowolne lub liczbowe.  
  
 `expression`  
 Wymagany. `Boolean`Wyrażenie dowolne lub liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku `Boolean` wyrażeń w poniższej tabeli pokazano, jak określono `result` .  
  
|Jeśli `expression` jest|Wartość `result` jest|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 W przypadku wyrażeń liczbowych `Not` operator odwraca wartości bitowe dowolnego wyrażenia liczbowego i ustawia odpowiedni bit w `result` zależności od poniższej tabeli.  
  
|Jeśli bit w `expression` jest|Bit w `result` jest|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
## <a name="data-types"></a>Typy danych  
 W przypadku negacji logicznej, typ danych wyniku to `Boolean` . W przypadku negacji bitowej dane wynikowe są takie same, jak w przypadku `expression` . Jeśli jednak wyrażenie ma wartość `Decimal` , wynik jest `Long` .  
  
## <a name="overloading"></a>Przeciążenie  
 `Not`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może zmienić jego zachowanie, gdy jego operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Not` operatora do wykonywania logiczne negacji dla `Boolean` wyrażenia. Wynik jest `Boolean` wartością, która reprezentuje odwracanie wartości wyrażenia.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Powyższy przykład daje wyniki `False` odpowiednio i `True` .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Not` operatora do wykonywania logicznego negacji poszczególnych bitów wyrażenia liczbowego. Bit w wzorcu wyniku jest ustawiony na odwrotność odpowiedniego bitu we wzorcu operandu, łącznie z bitem znaku.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Powyższy przykład daje wyniki odpowiednio – 11, – 9 i – 7.  
  
## <a name="see-also"></a>Zobacz też

- [Operatory logiczne/bitowe (Visual Basic)](logical-bitwise-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory logiczne i bitowe w Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
