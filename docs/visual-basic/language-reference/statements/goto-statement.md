---
title: "GoTo — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GoTo
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a>GoTo — Instrukcja
Przechodzi bezwarunkowo do określonego wiersza procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Część  
 `line`  
 Wymagany. Wszystkie wiersza etykiety.  
  
## <a name="remarks"></a>Uwagi  
 `GoTo` Instrukcji można rozgałęzić tylko wiersze w procedurze, w której znajduje się. Wiersz musi mieć etykietę linii `GoTo` mogą odwoływać się do. Aby uzyskać więcej informacji, zobacz [porady: Etykieta instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo`instrukcje może utrudnić kodu do odczytu i obsługi. Jeśli to możliwe, należy użyć Struktura kontroli. Aby uzyskać więcej informacji, zobacz [przepływ sterowania](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nie można użyć `GoTo` instrukcji do gałęzi poza `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, lub `Using`... `End Using` konstrukcji etykietę wewnątrz.  
  
## <a name="branching-and-try-constructions"></a>Rozgałęzianie i spróbuj konstrukcji  
 W ramach `Try`... `Catch`... `Finally` obowiązują następujące reguły konstrukcji, aby rozgałęziania z `GoTo` instrukcji.  
  
|Blokowanie lub region|Rozgałęziania w z poza|Rozgałęziania limit z wewnątrz|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`Blok|Tylko z `Catch` bloku o takiej samej konstrukcji <sup>1</sup>|Tylko poza całego konstrukcji|  
|`Catch`Blok|Nigdy nie są dozwolone|Tylko poza całego konstruowania lub do `Try` bloku o takiej samej konstrukcji <sup>1</sup>|  
|`Finally`Blok|Nigdy nie są dozwolone|Nigdy nie są dozwolone|  
  
 <sup>1</sup> jeden `Try`... `Catch`... `Finally` konstrukcji jest zagnieżdżony w innym, `Catch` bloku można rozgałęzić do `Try` bloku na jego własnej poziom zagnieżdżenia, ale nie do innych `Try` bloku. Zagnieżdżoną `Try`... `Catch`... `Finally` konstrukcji musi znajdować się całkowicie w `Try` lub `Catch` konstrukcji, w którym jest zagnieżdżony blok.  
  
 Na poniższej ilustracji przedstawiono jedną `Try` konstrukcji zagnieżdżone w innym. Różnych gałęzi między bloków dwa obiekty są oznaczone jako prawidłowy lub nieprawidłowy.  
  
 ![Graficzny diagram rozgałęzień w konstrukcjach Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Prawidłowe oraz nieprawidłowe gałęzie w konstrukcjach Try  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GoTo` instrukcji do gałęzi etykiet linii w procedurze.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Czy... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Dla... Next — instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [For Each... Next — instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [IF... Następnie... Else — instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Wybierz... Case-instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Try... CATCH... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [While... End While — instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Z... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
