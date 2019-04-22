---
title: Exit — Instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 1f386694bd7425ee530b9305ab684b730f9b73c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832635"
---
# <a name="exit-statement-visual-basic"></a>Exit — Instrukcja (Visual Basic)
Opuszcza procedurę lub blok i natychmiast przekazuje sterowanie do instrukcji następującej po wywołaniu procedury lub definicji bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Instrukcje  
 `Exit Do`  
 Natychmiast kończy działanie `Do` pętli, w którym pojawia się. Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `Loop` instrukcji. `Exit Do` można używać tylko wewnątrz `Do` pętli. Gdy jest używana w ramach zagnieżdżonych `Do` pętli, `Exit Do` opuszcza pętlę najbardziej i przekazuje sterowanie do następnego wyższy poziom zagnieżdżenia.  
  
 `Exit For`  
 Natychmiast kończy działanie `For` pętli, w którym pojawia się. Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `Next` instrukcji. `Exit For` można używać tylko wewnątrz `For`... `Next` lub `For Each`... `Next` pętli. Gdy jest używana w ramach zagnieżdżonych `For` pętli, `Exit For` opuszcza pętlę najbardziej i przekazuje sterowanie do następnego wyższy poziom zagnieżdżenia.  
  
 `Exit Function`  
 Natychmiast kończy działanie `Function` procedury, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała `Function` procedury. `Exit Function` można używać tylko wewnątrz `Function` procedury.  
  
 Aby określić wartość zwracana, można przypisać wartości do nazwy funkcji w wierszu przed `Exit Function` instrukcji. Aby przypisać wartość zwracaną i zakończyć działanie funkcji w jednej instrukcji, należy użyć [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Natychmiast kończy działanie `Property` procedury, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji, która wywołuje `Property` procedura, oznacza to, za pomocą instrukcji żądania lub ustawiania wartości właściwości. `Exit Property` można używać tylko wewnątrz właściwości `Get` lub `Set` procedury.  
  
 Aby określić wartości zwracanej w `Get` procedury, można przypisać wartości do nazwy funkcji w wierszu przed `Exit Property` instrukcji. Aby przypisać wartość zwracaną i zakończenia `Get` procedury w jednej instrukcji, należy użyć `Return` instrukcji.  
  
 W `Set` procedury `Exit Property` instrukcja jest odpowiednikiem `Return` instrukcji.  
  
 `Exit Select`  
 Natychmiast kończy działanie `Select Case` bloku, w którym pojawia się. Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `End Select` instrukcji. `Exit Select` można używać tylko wewnątrz `Select Case` instrukcji.  
  
 `Exit Sub`  
 Natychmiast kończy działanie `Sub` procedury, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała `Sub` procedury. `Exit Sub` można używać tylko wewnątrz `Sub` procedury.  
  
 W `Sub` procedury `Exit Sub` instrukcja jest odpowiednikiem `Return` instrukcji.  
  
 `Exit Try`  
 Natychmiast kończy działanie `Try` lub `Catch` bloku, w którym pojawia się. Wykonywanie jest kontynuowane przy użyciu `Finally` zablokować, jeśli istnieje, lub przy użyciu następujących instrukcji `End Try` instrukcji, w przeciwnym razie. `Exit Try` można używać tylko wewnątrz `Try` lub `Catch` bloku, a nie w obrębie `Finally` bloku.  
  
 `Exit While`  
 Natychmiast kończy działanie `While` pętli, w którym pojawia się. Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `End While` instrukcji. `Exit While` można używać tylko wewnątrz `While` pętli. Gdy jest używana w ramach zagnieżdżonych `While` pętli, `Exit While` przekazuje sterowanie do pętli, która znajduje się na poziomie zagnieżdżonych powyżej pętli gdzie `Exit While` występuje.  
  
## <a name="remarks"></a>Uwagi  
 Nie należy mylić `Exit` instrukcje `End` instrukcji. `Exit` Definiuje końcem instrukcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, warunek pętli zatrzymuje pętli po `index` zmiennej jest większa niż 100. `If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcję, aby zatrzymanie pętli, gdy zmienna index jest większy niż 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction`, a następnie używa `Exit Function` zostać zwrócony przez funkcję.  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md) do przypisywania wartości zwracanej i zakończyć działanie funkcji.  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Zobacz także

- [Continue, instrukcja](../../../visual-basic/language-reference/statements/continue-statement.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrukcja End](../../../visual-basic/language-reference/statements/end-statement.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Return, instrukcja](../../../visual-basic/language-reference/statements/return-statement.md)
- [Stop, instrukcja](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
