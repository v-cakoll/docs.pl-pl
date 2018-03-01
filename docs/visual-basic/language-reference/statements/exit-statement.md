---
title: "Exit — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a>Exit — Instrukcja (Visual Basic)
Opuszcza procedurę lub blok i natychmiast przenosi formantu do instrukcji następującej wywołanie procedury lub definicji bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Instrukcje  
 `Exit Do`  
 Natychmiast kończy pracę `Do` pętli, w którym pojawi się. Kontynuuje wykonywanie instrukcji następującej `Loop` instrukcji. `Exit Do`można używać tylko wewnątrz `Do` pętli. Gdy jest używany w zagnieżdżonych `Do` pętli, `Exit Do` kończy tryb pętli najbardziej i przekazuje sterowanie do następnego wyższego poziomu zagnieżdżenia.  
  
 `Exit For`  
 Natychmiast kończy pracę `For` pętli, w którym pojawi się. Kontynuuje wykonywanie instrukcji następującej `Next` instrukcji. `Exit For`można używać tylko wewnątrz `For`... `Next` lub `For Each`... `Next` pętli. Gdy jest używany w zagnieżdżonych `For` pętli, `Exit For` kończy tryb pętli najbardziej i przekazuje sterowanie do następnego wyższego poziomu zagnieżdżenia.  
  
 `Exit Function`  
 Natychmiast kończy pracę `Function` procedury, w których występuje. Kontynuuje wykonywanie instrukcji następującej po instrukcji, która wywołała `Function` procedury. `Exit Function`można używać tylko wewnątrz `Function` procedury.  
  
 Aby określić wartość zwracaną, można przypisać wartość Nazwa funkcji w wierszu przed `Exit Function` instrukcji. Aby przypisać wartości zwracanej i zakończyć działanie funkcji w jednej instrukcji, należy użyć [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Natychmiast kończy pracę `Property` procedury, w których występuje. Kontynuuje wykonywanie instrukcji, która wywołuje `Property` procedury, czyli z instrukcją żądania lub ustawiania wartości właściwości. `Exit Property`można używać tylko wewnątrz właściwości `Get` lub `Set` procedury.  
  
 Aby określić wartości zwracanej w `Get` procedury, można przypisać wartość Nazwa funkcji w wierszu przed `Exit Property` instrukcji. Można przypisać wartości zwracanej i zakończenia `Get` procedury w jednej instrukcji, należy użyć `Return` instrukcji.  
  
 W `Set` procedury `Exit Property` instrukcja jest odpowiednikiem `Return` instrukcji.  
  
 `Exit Select`  
 Natychmiast kończy pracę `Select Case` blok, w którym pojawi się. Kontynuuje wykonywanie instrukcji następującej `End Select` instrukcji. `Exit Select`można używać tylko wewnątrz `Select Case` instrukcji.  
  
 `Exit Sub`  
 Natychmiast kończy pracę `Sub` procedury, w których występuje. Kontynuuje wykonywanie instrukcji następującej po instrukcji, która wywołała `Sub` procedury. `Exit Sub`można używać tylko wewnątrz `Sub` procedury.  
  
 W `Sub` procedury `Exit Sub` instrukcja jest odpowiednikiem `Return` instrukcji.  
  
 `Exit Try`  
 Natychmiast kończy pracę `Try` lub `Catch` blok, w którym pojawi się. Kontynuuje wykonywanie `Finally` zablokować, jeśli istnieje, lub z następujących instrukcji `End Try` instrukcji w inny sposób. `Exit Try`można używać tylko wewnątrz `Try` lub `Catch` bloku, a nie do wewnątrz `Finally` bloku.  
  
 `Exit While`  
 Natychmiast kończy pracę `While` pętli, w którym pojawi się. Kontynuuje wykonywanie instrukcji następującej `End While` instrukcji. `Exit While`można używać tylko wewnątrz `While` pętli. Gdy jest używany w zagnieżdżonych `While` pętle, `Exit While` przekazuje sterowanie do pętli o jeden poziom zagnieżdżony powyżej pętli gdzie `Exit While` występuje.  
  
## <a name="remarks"></a>Uwagi  
 Nie należy mylić `Exit` instrukcji z `End` instrukcje. `Exit`nie definiuje końca instrukcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie warunek pętli zatrzymuje pętli podczas `index` zmiennej jest większa niż 100. `If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcji, aby zatrzymać pętli, gdy zmienna indeksu jest większa niż 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przypisuje wartość zwracaną nazwą funkcji `myFunction`, a następnie używa `Exit Function` ma zostać zwrócony przez funkcję.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) do przypisywania wartości zwracanej i zakończyć działanie funkcji.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Continue — instrukcja](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [Czy... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [End — instrukcja](../../../visual-basic/language-reference/statements/end-statement.md)  
 [For Each... Next — instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Dla... Next — instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return — instrukcja](../../../visual-basic/language-reference/statements/return-statement.md)  
 [Stop — instrukcja](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Try... CATCH... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
