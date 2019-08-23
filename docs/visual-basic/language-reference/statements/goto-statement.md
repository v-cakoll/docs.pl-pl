---
title: GoTo — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912449"
---
# <a name="goto-statement"></a>GoTo — Instrukcja
Rozgałęzienia bezwarunkowo do określonego wiersza procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Części  
 `line`  
 Wymagany. Dowolna etykieta wiersza.  
  
## <a name="remarks"></a>Uwagi  
 `GoTo` Instrukcja może rozgałęziać tylko do wierszy w procedurze, w której występuje. Wiersz musi mieć etykietę wiersza, która `GoTo` może odwoływać się do. Aby uzyskać więcej informacji, zobacz [jak: Instrukcje](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)etykiet.  
  
> [!NOTE]
> `GoTo`instrukcje mogą utrudniać odczytywanie i konserwację kodu. Jeśli to możliwe, zamiast tego użyj struktury formantu. Aby uzyskać więcej informacji, zobacz [sterowanie przepływem](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nie można użyć `GoTo` instrukcji do rozgałęzienia spoza elementu `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With` lub`Using`... `End Using` konstrukcja do etykiety wewnątrz.  
  
## <a name="branching-and-try-constructions"></a>Rozgałęzianie i próba konstrukcji  
 `Try`W... `Catch`... w celu rozgałęziania `GoTo` instrukcji należy zastosować następujące reguły. `Finally`  
  
|Blok lub region|Rozgałęzianie od zewnątrz|Rozgałęzianie od wewnątrz|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`odblokowan|Tylko z `Catch` bloku tej samej konstrukcji <sup>1</sup>|Tylko poza całością konstrukcji|  
|`Catch`odblokowan|Nigdy niedozwolone|Tylko poza całościową budową lub `Try` blokiem tej samej konstrukcji <sup>1</sup>|  
|`Finally`odblokowan|Nigdy niedozwolone|Nigdy niedozwolone|  
  
 <sup>1</sup> , jeśli `Try`jeden... `Catch`... konstrukcja jest zagnieżdżona w innym `Catch` , `Try` blok może odgałęzić się do bloku na jego własnym poziomie zagnieżdżenia, ale nie w `Try` żadnym innym bloku. `Finally` Zagnieżdżony `Try`... `Catch`... konstrukcja musi być całkowicie zawarta `Try` w `Catch` bloku lub konstrukcji, w której jest zagnieżdżona. `Finally`  
  
 Na poniższej ilustracji przedstawiono jedną `Try` konstrukcję zagnieżdżoną w innej. Różne gałęzie między blokami dwóch konstrukcji są wskazywane jako prawidłowe lub nieprawidłowe.  
  
 ![Diagram graficzny rozgałęzień w konstrukcjach try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `GoTo` instrukcji do rozgałęziania etykiet linii w procedurze.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także

- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrukcja Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
