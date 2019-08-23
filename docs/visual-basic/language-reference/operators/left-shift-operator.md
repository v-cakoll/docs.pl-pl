---
title: Operator < < (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: d6b186ad519bcd7cf82cce12523f2d75e09317cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966884"
---
# <a name="-operator-visual-basic"></a>\<\<Operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w lewo na wzorcu bitowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Całkowita wartość liczbowa. Wynik przesunięcia wzorca bitowego. Typ danych jest taki sam jak w przypadku programu `pattern`.  
  
 `pattern`  
 Wymagane. Całkowite wyrażenie liczbowe. Wzorzec bitowy, który ma zostać przesunięty. Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Integer` `UShort` `Short` `Long`,,, `ULong`, lub). `UInteger`  
  
 `amount`  
 Wymagany. Wyrażenie liczbowe. Liczba bitów do przesunięcia wzorca bitowego. Typ danych musi być lub `Integer` być rozszerzony do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. W przypadku przesunięcia w lewo po lewej stronie bity przesunięte poza zakres typu danych wynik są odrzucane, a pozycje bitowe opuszczone po prawej stronie są ustawione na wartość zero.  
  
 Aby zapobiec przesunięciu przez więcej bitów niż w wyniku, Visual Basic maskuje wartość `amount` z maską rozmiaru odpowiadającą `pattern`typowi danych. Wartość binarna i z tych wartości są używane na potrzeby przesunięcia. Maski rozmiaru są następujące:  
  
|Typ danych`pattern`|Maska rozmiaru (dziesiętna)|Maska rozmiaru (szesnastkowo)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Jeśli `amount` jest równa zero, `result` wartość jest `pattern`taka sama jak wartość. Jeśli `amount` jest ujemna, jest traktowana jako wartość bez znaku i zamaskowany przy odpowiedniej masce rozmiaru.  
  
 Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.  
  
> [!NOTE]
> Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `<<` Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `<<` aby przeprowadzić arytmetyczne przesunięcie w lewo na wartościach całkowitych. Wynik zawsze ma ten sam typ danych co w przypadku przesunięcia wyrażenia.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
- `result1`jest 192 (0000 0000 1100 0000).  
  
- `result2`jest 3072 (0000 1100 0000 0000).  
  
- `result3`is-32768 (1000 0000 0000 0000).  
  
- `result4`jest 384 (0000 0001 1000 0000).  
  
- `result5`jest 0 (przesunięte 15 miejsc w lewo).  
  
 Wartość przesunięcia dla `result4` jest obliczana jako 17 i 15, która jest równa 1.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<=, operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
