---
title: << — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 329cdf1aea9ca97db000bb5ced8d9e8d6b7a4f58
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970561"
---
# <a name="-operator-visual-basic"></a>\<\< — Operator (Visual Basic)
Dokonuje arytmetycznego przesunięcia w lewo wzorca bitowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Całkowitą wartość liczbową. Wynik przesunięcia wzorca bitowego. Typ danych jest taka sama jak w przypadku `pattern`.  
  
 `pattern`  
 Wymagana. Całkowite wyrażenia liczbowego. Wzorzec bitowy jest przesuwany. Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).  
  
 `amount`  
 Wymagana. Wyrażenie liczbowe. Liczba bitów do przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub mogą zostać poszerzone do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie. W arytmetyczne przesunięcie w lewo bity przesunięte poza zakresem typu danych wyniku są odrzucane i pozycje bitów zwolnione w wyniku po prawej stronie zostaną ustawione na zero.  
  
 Aby zapobiec shift przez kilka bitów, niż może pomieścić wynik, Visual Basic maskuje wartość `amount` za pomocą maski rozmiar, który odnosi się do typu danych `pattern`. Liczba przesunięć służy binarne i tych wartości. Maski rozmiar są następujące:  
  
|Typ danych `pattern`|Rozmiar maski (dziesiętna)|Maska rozmiar (w formacie szesnastkowym)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Jeśli `amount` jest równy zero, wartość `result` jest taka sama jak wartość `pattern`. Jeśli `amount` jest ujemna, jest traktowana jako wartość nieoznaczona i maskowane symbolami maska odpowiedniego rozmiaru.  
  
 Arytmetycznego przesunięcia nigdy nie generują wyjątki przepełnienia.  
  
> [!NOTE]
>  `<<` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, pamiętaj, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `<<` operator, aby wykonać arytmetyki lewo przesunięcia na wartości całkowitych. Wynik ma zawsze taki sam typ jak wyrażenie inne danych.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Wyniki z poprzedniego przykładu są następujące:  
  
-   `result1` jest 192 (0000 0000 1100 0000).  
  
-   `result2` to 3072 (0000 1100 0000 0000).  
  
-   `result3` to od -32768 (1000 0000 0000 0000).  
  
-   `result4` jest 384 (0000 0001 1000 0000).  
  
-   `result5` to 0 (przesuniętych 15 miejsca po lewej stronie).  
  
 Liczba przesunięć dla `result4` jest obliczany jako 17 i 15, która jest równa 1.  
  
## <a name="see-also"></a>Zobacz także
- [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<=, operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
