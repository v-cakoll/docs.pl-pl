---
title: '>> — Operator (Visual Basic)'
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
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816970"
---
# <a name="-operator-visual-basic"></a>>> — Operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w prawo przy użyciu wzorca bitowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Całkowitą wartość liczbową. Wynik przesunięcia wzorca bitowego. Typ danych jest taka sama jak w przypadku `pattern`.  
  
 `pattern`  
 Wymagana. Całkowite wyrażenia liczbowego. Wzorzec bitowy jest przesuwany. Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).  
  
 `amount`  
 Wymagana. Wyrażenie liczbowe. Liczba bitów do przesunięcia wzorca bitowego. Typ danych musi być `Integer` lub mogą zostać poszerzone do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie. W arytmetyczne przesunięcie w prawo bity przesunięte poza Pozycja bitu po prawej stronie są odrzucane i bitu skrajnie po lewej stronie (znak) jest propagowana do pozycji bitów zwolnione w wyniku po lewej stronie. Oznacza to, że jeśli `pattern` ma wartość ujemną, opuszczone pozycje są ustawione na jedną; w przeciwnym razie zostaną ustawione na zero.  
  
 Należy pamiętać, że typy danych `Byte`, `UShort`, `UInteger`, i `ULong` są bez znaku, więc nie ma żadnych bitu znaku do propagowania. Jeśli `pattern` jest dowolny bez znaku typu, opuszczone pozycje są zawsze ustawione na zero.  
  
 Aby zapobiec przesunięcie przez kilka bitów, niż może pomieścić wynik, Visual Basic maskuje wartość `amount` za pomocą maski rozmiar odpowiadający typowi danych z `pattern`. Liczba przesunięć służy binarne i tych wartości. Maski rozmiar są następujące:  
  
|Typ danych `pattern`|Rozmiar maski (dziesiętna)|Maska rozmiar (w formacie szesnastkowym)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Jeśli `amount` jest równy zero, wartość `result` jest taka sama jak wartość `pattern`. Jeśli `amount` jest ujemna, jest traktowana jako wartość nieoznaczona i maskowane symbolami maska odpowiedniego rozmiaru.  
  
 Arytmetycznego przesunięcia nigdy nie generują wyjątki przepełnienia.  
  
## <a name="overloading"></a>Przeciążenie  
 `>>` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `>>` operatora do wykonania arytmetycznego przesunięcia w prawo w wartości całkowitych. Wynik ma zawsze taki sam typ jak wyrażenie inne danych.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
-   `result1` jest 2560 (0000 1010 0000 0000).  
  
-   `result2` jest 160 (0000 0000 1010 0000).  
  
-   `result3` to 2 (0000 0000 0000 0010).  
  
-   `result4` to 640 (0000 0010 1000 0000).  
  
-   `result5` to 0 (przesuniętych 15 miejsc z prawej strony).  
  
 Liczba przesunięć dla `result4` jest obliczany jako 18 i 15, która jest równa 2.  
  
 Poniższy przykład pokazuje arytmetycznego przesunięcia na wartość ujemną.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Wyniki poprzedniego przykładu są następujące:  
  
-   `negresult1` jest-512 (1111 1110 0000 0000).  
  
-   `negresult2` wynosi -1 (propagowane bitem znaku).  
  
## <a name="see-also"></a>Zobacz także

- [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>=, operator](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
