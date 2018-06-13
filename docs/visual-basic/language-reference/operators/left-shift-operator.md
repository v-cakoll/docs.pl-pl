---
title: '&lt;&lt; — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: bdec015309526aeac2499bc7b459b6ccab6f1e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604461"
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt; — Operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w lewo na ciągu bitowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Całkowite wartość liczbowa. Wynik przesunięcia wzorca bitowego. Typ danych jest taki sam, jak te `pattern`.  
  
 `pattern`  
 Wymagana. Całkowite wyrażenia liczbowego. Wzorca bitowego lekkie. Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).  
  
 `amount`  
 Wymagana. Wyrażenie liczbowe. Liczba bitów przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub rozszerzyć do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bitów przesunąć poza jednym zakończeniu wynik nie są ponownie na drugim końcu. W arytmetyczne przesunięcie w lewo bitów przesunięty poza zakresem typu danych zostaną odrzucone i pozycji z bitowego vacated po prawej stronie zostaną ustawione na zero.  
  
 Aby zapobiec shift przez bits więcej niż wynik może pomieścić, Visual Basic maski wartość `amount` za pomocą maski rozmiar, która odnosi się do typu danych `pattern`. Binarne i tych wartości jest używany dla wielkość przesunięcia. Rozmiar maski są następujące:  
  
|Typ danych `pattern`|Rozmiar maski (dziesiętna)|Rozmiar maski (szesnastkowo)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|15|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 Jeśli `amount` jest zero, wartość `result` jest taka sama jak wartość `pattern`. Jeśli `amount` jest ujemna, jest traktowana jako wartość bez znaku i maskowane maska odpowiedni rozmiar.  
  
 Arytmetycznego przesunięcia nigdy nie generowanie wyjątków przepełnienia.  
  
> [!NOTE]
>  `<<` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, należy się zapoznać z jego zachowanie ponownie zdefiniowany. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `<<` operatora, aby wykonać arytmetyki przesunięcia w lewo na wartościach całkowitych. Wynik ma zawsze taki sam typ jak inne wyrażenia danych.  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
-   `result1` jest 192 (0000 0000 1100 0000).  
  
-   `result2` jest 3072 (0000 1100 0000 0000).  
  
-   `result3` jest -32768 (1000 0000 0000 0000).  
  
-   `result4` jest 384 (0000 0001 1000 0000).  
  
-   `result5` to 0 (przesuniętych 15 miejsca po lewej stronie).  
  
 Liczba przesunięć dla `result4` jest obliczany jako 17 i 15, która jest równa 1.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<<=, operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
