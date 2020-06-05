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
ms.openlocfilehash: 1128b32a739e7dbf3893dcd19b37247cd4643c85
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370638"
---
# <a name="-operator-visual-basic"></a>\<\<Operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w lewo na wzorcu bitowym.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Całkowita wartość liczbowa. Wynik przesunięcia wzorca bitowego. Typ danych jest taki sam jak w przypadku programu `pattern` .  
  
 `pattern`  
 Wymagany. Całkowite wyrażenie liczbowe. Wzorzec bitowy, który ma zostać przesunięty. Typ danych musi być typem całkowitym (,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` , `Long` lub `ULong` ).  
  
 `amount`  
 Wymagany. Wyrażenie liczbowe. Liczba bitów do przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub być rozszerzony do `Integer` .  
  
## <a name="remarks"></a>Uwagi  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. W przypadku przesunięcia w lewo po lewej stronie bity przesunięte poza zakres typu danych wynik są odrzucane, a pozycje bitowe opuszczone po prawej stronie są ustawione na wartość zero.  
  
 Aby zapobiec przesunięciu przez więcej bitów niż w wyniku, Visual Basic maskuje wartość `amount` z maską rozmiaru odpowiadającą typowi danych `pattern` . Wartość binarna i z tych wartości są używane na potrzeby przesunięcia. Maski rozmiaru są następujące:  
  
|Typ danych`pattern`|Maska rozmiaru (dziesiętna)|Maska rozmiaru (szesnastkowo)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Jeśli `amount` jest równa zero, wartość `result` jest taka sama jak wartość `pattern` . Jeśli `amount` jest ujemna, jest traktowana jako wartość bez znaku i zamaskowany przy odpowiedniej masce rozmiaru.  
  
 Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.  
  
> [!NOTE]
> `<<`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `<<` Aby przeprowadzić arytmetyczne przesunięcie w lewo na wartościach całkowitych. Wynik zawsze ma ten sam typ danych co w przypadku przesunięcia wyrażenia.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
- `result1`jest 192 (0000 0000 1100 0000).  
  
- `result2`jest 3072 (0000 1100 0000 0000).  
  
- `result3`is-32768 (1000 0000 0000 0000).  
  
- `result4`jest 384 (0000 0001 1000 0000).  
  
- `result5`jest 0 (przesunięte 15 miejsc w lewo).  
  
 Wartość przesunięcia dla `result4` jest obliczana jako 17 i 15, która jest równa 1.  
  
## <a name="see-also"></a>Zobacz też

- [Operatory Bit Shift](bit-shift-operators.md)
- [Operatory przypisania](assignment-operators.md)
- [<<= — operator](left-shift-assignment-operator.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
