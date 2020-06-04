---
title: GoTo — Instrukcja
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
ms.openlocfilehash: eb6f48d04b7d14591003e340464451da7df45cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404618"
---
# <a name="goto-statement"></a>GoTo — Instrukcja
Rozgałęzienia bezwarunkowo do określonego wiersza procedury.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Część  
 `line`  
 Wymagany. Dowolna etykieta wiersza.  
  
## <a name="remarks"></a>Uwagi  
 `GoTo`Instrukcja może rozgałęziać tylko do wierszy w procedurze, w której występuje. Wiersz musi mieć etykietę wiersza, która `GoTo` może odwoływać się do. Aby uzyskać więcej informacji, zobacz [instrukcje: etykietowanie instrukcji](../../programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo`instrukcje mogą utrudniać odczytywanie i konserwację kodu. Jeśli to możliwe, zamiast tego użyj struktury formantu. Aby uzyskać więcej informacji, zobacz [sterowanie przepływem](../../programming-guide/language-features/control-flow/index.md).  
  
 Nie można użyć `GoTo` instrukcji do rozgałęzienia spoza elementu `For` ... `Next` , `For Each` ... `Next` , `SyncLock` . `End SyncLock` `Try` `Catch` ..,... ... `Finally` , `With` ... `End With` , lub `Using` ... `End Using` konstrukcja do etykiety wewnątrz.  
  
## <a name="branching-and-try-constructions"></a>Rozgałęzianie i próba konstrukcji  
 W `Try` ... `Catch` ...`Finally` w celu rozgałęziania instrukcji należy zastosować następujące reguły `GoTo` .  
  
|Blok lub region|Rozgałęzianie od zewnątrz|Rozgałęzianie od wewnątrz|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`odblokowan|Tylko z `Catch` bloku tej samej konstrukcji <sup>1</sup>|Tylko poza całością konstrukcji|  
|`Catch`odblokowan|Nigdy niedozwolone|Tylko poza całościową budową lub `Try` blokiem tej samej konstrukcji <sup>1</sup>|  
|`Finally`odblokowan|Nigdy niedozwolone|Nigdy niedozwolone|  
  
 <sup>1</sup> , jeśli jeden `Try` ... `Catch` ...`Finally` konstrukcja jest zagnieżdżona w innym, `Catch` blok może odgałęzić się do `Try` bloku na jego własnym poziomie zagnieżdżenia, ale nie w żadnym innym `Try` bloku. Zagnieżdżony `Try` ... `Catch` ...`Finally` konstrukcja musi być całkowicie zawarta `Try` w `Catch` bloku lub konstrukcji, w której jest zagnieżdżona.  
  
 Na poniższej ilustracji przedstawiono jedną `Try` konstrukcję zagnieżdżoną w innej. Różne gałęzie między blokami dwóch konstrukcji są wskazywane jako prawidłowe lub nieprawidłowe.  
  
 ![Diagram graficzny rozgałęzień w konstrukcjach try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `GoTo` instrukcji do rozgałęziania etykiet linii w procedurze.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz też

- [Do...Loop, instrukcja](do-loop-statement.md)
- [For...Next, instrukcja](for-next-statement.md)
- [For Each...Next, instrukcja](for-each-next-statement.md)
- [If...Then...Else, instrukcja](if-then-else-statement.md)
- [Select...Case, instrukcja](select-case-statement.md)
- [Try...Catch...Finally, instrukcja](try-catch-finally-statement.md)
- [While...End While, instrukcja](while-end-while-statement.md)
- [With...End With, instrukcja](with-end-with-statement.md)
