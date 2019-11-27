---
title: <<, operator
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 327d0e5cbd1ebcc43bd47fb068f4513940c2165a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350980"
---
# <a name="-operator-visual-basic"></a>Operator \< \<(Visual Basic)
Wykonuje arytmetyczne przesunięcie w lewo na wzorcu bitowym.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Całkowita wartość liczbowa. Wynik przesunięcia wzorca bitowego. Typ danych jest taki sam jak w przypadku `pattern`.  
  
 `pattern`  
 Wymagany. Całkowite wyrażenie liczbowe. Wzorzec bitowy, który ma zostać przesunięty. Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`lub `ULong`).  
  
 `amount`  
 Wymagany. Wyrażenie liczbowe. Liczba bitów do przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub rozszerzony do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. W przypadku przesunięcia w lewo po lewej stronie bity przesunięte poza zakres typu danych wynik są odrzucane, a pozycje bitowe opuszczone po prawej stronie są ustawione na wartość zero.  
  
 Aby zapobiec przesunięciu przez więcej bitów, niż można obtrzymać, Visual Basic maskować wartość `amount` z maską rozmiaru odpowiadającą typowi danych `pattern`. Wartość binarna i z tych wartości są używane na potrzeby przesunięcia. Maski rozmiaru są następujące:  
  
|Typ danych `pattern`|Maska rozmiaru (dziesiętna)|Maska rozmiaru (szesnastkowo)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Jeśli `amount` wynosi zero, wartość `result` jest taka sama jak wartość `pattern`. Jeśli `amount` jest ujemna, jest traktowany jako wartość bez znaku i maskowany z odpowiednią maską rozmiaru.  
  
 Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.  
  
> [!NOTE]
> Operator `<<` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `<<`, aby przeprowadzić arytmetyczne przesunięcie w lewo na wartościach całkowitych. Wynik zawsze ma ten sam typ danych co w przypadku przesunięcia wyrażenia.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
- `result1` to 192 (0000 0000 1100 0000).  
  
- `result2` to 3072 (0000 1100 0000 0000).  
  
- `result3` to-32768 (1000 0000 0000 0000).  
  
- `result4` to 384 (0000 0001 1000 0000).  
  
- `result5` to 0 (przesunięte 15 miejsc w lewo).  
  
 Kwota przesunięcia dla `result4` jest obliczana jako 17 i 15, która jest równa 1.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<=, operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
