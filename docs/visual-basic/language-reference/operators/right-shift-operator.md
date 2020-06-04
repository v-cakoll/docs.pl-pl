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
ms.openlocfilehash: 10b07da22b8b43d6a966fa7c334ac6a0ef4b430d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406374"
---
# <a name="-operator-visual-basic"></a>Operator >> (Visual Basic)
Wykonuje arytmetyczne przesunięcie w prawo na wzorcu bitowym.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Całkowita wartość liczbowa. Wynik przesunięcia wzorca bitowego. Typ danych jest taki sam jak w przypadku programu `pattern` .  
  
 `pattern`  
 Wymagany. Całkowite wyrażenie liczbowe. Wzorzec bitowy, który ma zostać przesunięty. Typ danych musi być typem całkowitym (,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` , `Long` lub `ULong` ).  
  
 `amount`  
 Wymagany. Wyrażenie liczbowe. Liczba bitów do przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub być rozszerzony do `Integer` .  
  
## <a name="remarks"></a>Uwagi  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. W wyniku przesunięcia w prawo, bity przesunięte poza skrajną prawą pozycję bitową są odrzucane, a w lewej (znak) bit jest propagowany do pozycji bitowych opuszczone. Oznacza to, że jeśli `pattern` ma wartość ujemną, pozycje opuszczone są ustawione na jeden; w przeciwnym razie są ustawione na wartość zero.  
  
 Należy zauważyć, że typy danych `Byte` ,, `UShort` `UInteger` i `ULong` są niepodpisane, dlatego nie istnieje bit znaku do propagowania. Jeśli `pattern` jest dowolnego typu bez znaku, pozycje opuszczone są zawsze ustawione na zero.  
  
 Aby zapobiec przesunięciu przez więcej bitów niż w wyniku, Visual Basic maskuje wartość `amount` z maską rozmiaru odpowiadającą typowi danych `pattern` . Wartość binarna i z tych wartości są używane na potrzeby przesunięcia. Maski rozmiaru są następujące:  
  
|Typ danych`pattern`|Maska rozmiaru (dziesiętna)|Maska rozmiaru (szesnastkowo)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Jeśli `amount` jest równa zero, wartość `result` jest taka sama jak wartość `pattern` . Jeśli `amount` jest ujemna, jest traktowana jako wartość bez znaku i zamaskowany przy odpowiedniej masce rozmiaru.  
  
 Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.  
  
## <a name="overloading"></a>Przeciążenie  
 `>>`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `>>` Aby wykonać arytmetyczne przesunięcie w prawo na wartościach całkowitych. Wynik zawsze ma ten sam typ danych co w przypadku przesunięcia wyrażenia.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 W powyższym przykładzie przedstawiono następujące wyniki:  
  
- `result1`jest 2560 (0000 1010 0000 0000).  
  
- `result2`jest 160 (0000 0000 1010 0000).  
  
- `result3`jest 2 (0000 0000 0000 0010).  
  
- `result4`jest 640 (0000 0010 1000 0000).  
  
- `result5`jest 0 (przesunięte 15 miejsc w prawo).  
  
 Wartość przesunięcia dla `result4` jest obliczana jako 18 i 15, która jest równa 2.  
  
 W poniższym przykładzie pokazano arytmetyczne przesunięcia na wartość ujemną.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 W powyższym przykładzie przedstawiono następujące wyniki:  
  
- `negresult1`is-512 (1111 1110 0000 0000).  
  
- `negresult2`is-1 (jest propagowany bit znaku).  
  
## <a name="see-also"></a>Zobacz też

- [Operatory Bit Shift](bit-shift-operators.md)
- [Operatory przypisania](assignment-operators.md)
- [>>= — operator](right-shift-assignment-operator.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
