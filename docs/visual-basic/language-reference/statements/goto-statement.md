---
title: GoTo — instrukcja (Visual Basic)
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
ms.openlocfilehash: 729ff2a9cbeacaefdf0452a6c5868c229a8d05b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582529"
---
# <a name="goto-statement"></a>GoTo — Instrukcja
Gałęzie przechodzi bezwarunkowo do określonego wiersza procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Część  
 `line`  
 Wymagana. Jakakolwiek etykieta wiersza.  
  
## <a name="remarks"></a>Uwagi  
 `GoTo` Instrukcji można rozgałęziać tylko do wierszy w procedurze, w której występuje. Wiersz musi mieć wiersz etykiety, która `GoTo` mogą odwoływać się do. Aby uzyskać więcej informacji, zobacz [jak: Etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo` instrukcje może utrudnić kodu do odczytu i obsługi. Jeśli to możliwe, należy użyć struktury sterowania. Aby uzyskać więcej informacji, zobacz [przepływ sterowania](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nie można użyć `GoTo` instrukcji gałęzi z poza `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, lub `Using`... `End Using` konstrukcji do etykiety wewnątrz.  
  
## <a name="branching-and-try-constructions"></a>Rozgałęzianie i spróbuj konstrukcji  
 W ramach `Try`... `Catch`... `Finally` konstrukcji, obowiązują następujące reguły do gałęzi z `GoTo` instrukcji.  
  
|Blokowanie lub region|Rozgałęziania w z zewnątrz|Rozgałęziania się od wewnątrz|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` Blok|Tylko z `Catch` bloku o takiej samej konstrukcji <sup>1</sup>|Tylko z poza całego konstrukcji|  
|`Catch` Blok|Nigdy nie jest dozwolone|Tylko z poza całego konstrukcja lub do `Try` bloku o takiej samej konstrukcji <sup>1</sup>|  
|`Finally` Blok|Nigdy nie jest dozwolone|Nigdy nie jest dozwolone|  
  
 <sup>1</sup> Jeśli `Try`... `Catch`... `Finally` konstrukcja jest zagnieżdżony w innym ciągu, `Catch` bloku można rozgałęzić do `Try` bloku swój własny poziom zagnieżdżenia, ale nie do innych `Try` bloku. Zagnieżdżone `Try`... `Catch`... `Finally` konstrukcji, które musi znajdować się całkowicie w `Try` lub `Catch` bloku konstruowania, w którym jest zagnieżdżony.  
  
 Poniższa ilustracja przedstawia jedną `Try` konstrukcji zagnieżdżona w innej. Różnych gałęziach między bloki konstrukcyjne dwa obiekty są oznaczone jako prawidłowy lub nieprawidłowy.  
  
 ![Graficzny diagram rozgałęzień w konstrukcji Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Prawidłowe i nieprawidłowe gałęzi, skorzystaj z konstrukcji Try  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GoTo` instrukcję, aby gałąź do etykiet linii w procedurze.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrukcja Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
