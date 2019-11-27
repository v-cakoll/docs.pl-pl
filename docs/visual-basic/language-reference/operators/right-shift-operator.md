---
title: '>> Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: cabf8c569435cc0fc98282f5e8f5fd410e6708dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347822"
---
# <a name="-operator-visual-basic"></a>Operator > > (Visual Basic)
Wykonuje arytmetyczne przesunięcie w prawo na wzorcu bitowym.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Całkowita wartość liczbowa. Wynik przesunięcia wzorca bitowego. Typ danych jest taki sam jak w przypadku `pattern`.  
  
 `pattern`  
 Wymagana. Całkowite wyrażenie liczbowe. Wzorzec bitowy, który ma zostać przesunięty. Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`lub `ULong`).  
  
 `amount`  
 Wymagana. Wyrażenie liczbowe. Liczba bitów do przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub rozszerzony do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. W wyniku przesunięcia w prawo, bity przesunięte poza skrajną prawą pozycję bitową są odrzucane, a w lewej (znak) bit jest propagowany do pozycji bitowych opuszczone. Oznacza to, że jeśli `pattern` ma wartość ujemną, pozycje opuszczone są ustawione na jeden. w przeciwnym razie jest ustawiona na zero.  
  
 Należy zauważyć, że typy danych `Byte`, `UShort`, `UInteger`i `ULong` są niepodpisane, więc nie istnieje bit znaku do propagowania. Jeśli `pattern` jest dowolnego typu bez znaku, pozycje opuszczone są zawsze ustawione na zero.  
  
 Aby zapobiec przesunięciu przez więcej bitów, niż można obsłużyć, Visual Basic maskować wartość `amount` z maską rozmiaru odpowiadającą typowi danych `pattern`. Wartość binarna i z tych wartości są używane na potrzeby przesunięcia. Maski rozmiaru są następujące:  
  
|Typ danych `pattern`|Maska rozmiaru (dziesiętna)|Maska rozmiaru (szesnastkowo)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Jeśli `amount` wynosi zero, wartość `result` jest taka sama jak wartość `pattern`. Jeśli `amount` jest ujemna, jest traktowany jako wartość bez znaku i maskowany z odpowiednią maską rozmiaru.  
  
 Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.  
  
## <a name="overloading"></a>Przeciążenie  
 Operator `>>` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `>>`, aby wykonać arytmetyczne przesunięcie w prawo na wartościach całkowitych. Wynik zawsze ma ten sam typ danych co w przypadku przesunięcia wyrażenia.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 W powyższym przykładzie przedstawiono następujące wyniki:  
  
- `result1` to 2560 (0000 1010 0000 0000).  
  
- `result2` to 160 (0000 0000 1010 0000).  
  
- `result3` to 2 (0000 0000 0000 0010).  
  
- `result4` to 640 (0000 0010 1000 0000).  
  
- `result5` to 0 (przesunięte 15 miejsc w prawo).  
  
 Kwota przesunięcia dla `result4` jest obliczana jako 18 i 15, która jest równa 2.  
  
 W poniższym przykładzie pokazano arytmetyczne przesunięcia na wartość ujemną.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 W powyższym przykładzie przedstawiono następujące wyniki:  
  
- `negresult1` to-512 (1111 1110 0000 0000).  
  
- `negresult2` to-1 (jest propagowany bit znaku).  
  
## <a name="see-also"></a>Zobacz także

- [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>=, operator](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
