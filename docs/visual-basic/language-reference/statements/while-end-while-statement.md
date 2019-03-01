---
title: While...End While — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 269a4c0f069b3837959b04f8463f96e7c5d5fdf7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970153"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While — Instrukcja (Visual Basic)
Uruchamia serię instrukcji tak długo, jak jest dany warunek `True`.  
  
## <a name="syntax"></a>Składnia  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`condition`|Wymagana. `Boolean` wyrażenie. Jeśli `condition` jest `Nothing`, Visual Basic traktuje je jako `False`.|  
|`statements`|Opcjonalna. Jeden lub więcej następujących instrukcji `While`, uruchamiania każdym `condition` jest `True`.|  
|`Continue While`|Opcjonalna. Przekazuje sterowanie do następnej iteracji `While` bloku.|  
|`Exit While`|Opcjonalna. Przekazuje sterowanie poza `While` bloku.|  
|`End While`|Wymagana. Kończy definicję `While` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `While...End While` struktury, gdy chcesz powtórzyć zbiór instrukcji na nieokreśloną liczbę razy, tak długo, jak długo pozostaje warunek `True`. Jeśli chcesz, większą elastyczność, gdy test warunku lub co powoduje, możesz ją przetestować, aby możesz preferować [zrobić... Instrukcja pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md). Jeśli chcesz powtórzyć oświadczeń określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) zazwyczaj jest lepszym rozwiązaniem.  
  
> [!NOTE]
>  `While` — Słowo kluczowe jest również używany w [zrobić... Instrukcja pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While — klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [Take While — klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Jeśli `condition` jest `True`, wszystkie z `statements` wykonywania do momentu `End While` napotkania instrukcji. Następnie zwraca do kontrolowania `While` instrukcji i `condition` zaznaczono opcję ponownie. Jeśli `condition` jest nadal `True`, proces jest powtarzany. Jeśli ma on `False`, kontrola przechodzi do instrukcji następującej `End While` instrukcji.  
  
 `While` Instrukcja zawsze sprawdza warunek, zanim zacznie pętli. Tworzenie pętli będzie się powtarzać, gdy warunek jest `True`. Jeśli `condition` jest `False` podczas wpisywania pętli nie działa ona jeszcze raz.  
  
 `condition` Zazwyczaj wynikiem porównania dwóch wartości, ale może być dowolne wyrażenie, które daje w wyniku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`). To wyrażenie może zawierać wartości innego typu danych, takich jak typ liczbowy, który został przekonwertowany na `Boolean`.  
  
 Można zagnieżdżać `While` pętli przez umieszczenie pętli w innym. Można także zagnieżdżać różne rodzaje struktur sterujących w ramach siebie nawzajem. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Zakończ podczas  
 [Wyjść, gdy](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji może zapewnić innym sposobem, aby zakończyć działanie `While` pętli. `Exit While` natychmiast przekazuje sterowanie do instrukcji następującej `End While` instrukcji.  
  
 Zazwyczaj używa się `Exit While` po ocenieniu jakiś warunek (na przykład w `If...Then...Else` struktury). Można zamknąć pętli, jeśli wykryje warunek, który sprawia, że niepotrzebnych lub niemożliwe kontynuować, iteracja, np. Błędna wartość lub żądanie zakończenia działania. Możesz użyć `Exit While` podczas testowania dla warunku, który może powodować *nieskończoną pętlę*, czyli pętlę, która może działać bardzo duże lub nawet nieskończona liczba prób. Następnie można użyć `Exit While` jako znak ucieczki dla pętli.  
  
 Można umieścić dowolną liczbę `Exit While` instrukcji w `While` pętli.  
  
 Gdy jest używana w ramach zagnieżdżonych `While` pętli, `Exit While` przenosi sterowanie na dostęp do najaktualniejszych najbardziej wewnętrznej i do następnego wyższy poziom zagnieżdżenia.  
  
 `Continue While` Instrukcji natychmiast przekazuje sterowanie do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [nadal instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli nadal działać do momentu `index` zmiennej jest większa niż 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie `Continue While` i `Exit While` instrukcji.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. <xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> , odczytuje znaki. W `While` warunku <xref:System.IO.StreamReader.Peek%2A> metody `StreamReader` Określa, czy plik zawiera dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Zobacz także
- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue, instrukcja](../../../visual-basic/language-reference/statements/continue-statement.md)
