---
title: '&gt;&gt; — Operator (Visual Basic)'
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
ms.openlocfilehash: 9bb8e82b3f5451417fe1867d08b7601ee1acb036
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605410"
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt; — Operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w prawo na ciągu bitowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Całkowite wartość liczbowa. Wynik przesunięcia wzorca bitowego. Typ danych jest taki sam, jak te `pattern`.  
  
 `pattern`  
 Wymagana. Całkowite wyrażenia liczbowego. Wzorca bitowego lekkie. Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).  
  
 `amount`  
 Wymagana. Wyrażenie liczbowe. Liczba bitów przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub rozszerzyć do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bitów przesunąć poza jednym zakończeniu wynik nie są ponownie na drugim końcu. W arytmetyczne przesunięcie w prawo bitów przesunięty poza Pozycja bitu po prawej stronie zostaną odrzucone i lewej strony (znaku) jest propagowana do pozycji z bitowego vacated po lewej stronie. Oznacza to, że jeśli `pattern` ma wartość ujemną vacated pozycje są ustawione na jedną; w przeciwnym razie zostaną ustawione na zero.  
  
 Należy pamiętać, że typy danych `Byte`, `UShort`, `UInteger`, i `ULong` nie mają znaku, więc nie ma żadnych bitem propagacji. Jeśli `pattern` jest niepodpisane dowolnego typu, vacated pozycji zawsze są ustawione na zero.  
  
 Aby uniemożliwić ich przesuwanie przez bits więcej niż wynik może pomieścić, Visual Basic maski wartość `amount` za pomocą maski rozmiar odpowiadający typ danych `pattern`. Binarne i tych wartości jest używany dla wielkość przesunięcia. Rozmiar maski są następujące:  
  
|Typ danych `pattern`|Rozmiar maski (dziesiętna)|Rozmiar maski (szesnastkowo)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|15|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 Jeśli `amount` jest zero, wartość `result` jest taka sama jak wartość `pattern`. Jeśli `amount` jest ujemna, jest traktowana jako wartość bez znaku i maskowane maska odpowiedni rozmiar.  
  
 Arytmetycznego przesunięcia nigdy nie generowanie wyjątków przepełnienia.  
  
## <a name="overloading"></a>Przeciążenie  
 `>>` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `>>` operatora, aby wykonać arytmetycznego przesunięcia w prawo w wartości całkowite. Wynik ma zawsze taki sam typ jak inne wyrażenia danych.  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
-   `result1` jest 2560 (0000 1010 0000 0000).  
  
-   `result2` jest 160 (0000 0000 1010 0000).  
  
-   `result3` to 2 (0000 0000 0000 0010).  
  
-   `result4` jest 640 (0000 0010 1000 0000).  
  
-   `result5` to 0 (przesuniętych 15 miejsca z prawej strony).  
  
 Liczba przesunięć dla `result4` jest obliczany jako 18 15 i, która jest równa 2.  
  
 W poniższym przykładzie przedstawiono arytmetycznego przesunięcia na wartość ujemną.  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
-   `negresult1` jest-512 (1111 1110 0000 0000).  
  
-   `negresult2` wynosi -1 (propagowane bitem).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [>>=, operator](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
