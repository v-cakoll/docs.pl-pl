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
ms.openlocfilehash: 9f46a6ec65faef4448bdd25e30a6cc0c605cd0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
|`condition`|Wymagana. `Boolean` Wyrażenie. Jeśli `condition` jest `Nothing`, Visual Basic traktuje ją jako `False`.|  
|`statements`|Opcjonalna. Jeden lub więcej następujących instrukcji `While`, uruchamiania zawsze `condition` jest `True`.|  
|`Continue While`|Opcjonalna. Przekazuje sterowanie do następnej iteracji `While` bloku.|  
|`Exit While`|Opcjonalna. Przekazuje sterowanie poza `While` bloku.|  
|`End While`|Wymagana. Kończy definicję `While` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `While...End While` struktury, gdy ma zostać powtórzony zestaw instrukcji o nieograniczonej liczby godzin, warunek nie zostanie `True`. Jeśli chcesz bardziej elastyczne, z którym testować warunek lub to, co powoduje, należy przetestować go dla łączyli [czy... Pętla instrukcji](../../../visual-basic/language-reference/statements/do-loop-statement.md). Jeśli chcesz powtarzać instrukcje jest określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszym rozwiązaniem.  
  
> [!NOTE]
>  `While` — Słowo kluczowe jest również używana w [czy... Pętla instrukcji](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While — klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [Take While — klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Jeśli `condition` jest `True`, wszystkie z `statements` do wykonywania `End While` napotkano instrukcji. Zwraca do kontrolowania `While` instrukcji i `condition` ponownie jest zaznaczony. Jeśli `condition` jest nadal `True`, proces jest powtarzany. Jeśli ma ona `False`, kontrola przechodzi do instrukcji następującej `End While` instrukcji.  
  
 `While` Przed uruchomieniem jej pętli instrukcji zawsze sprawdza warunek. Zapętlenie będzie nadal występować, gdy warunek jest `True`. Jeśli `condition` jest `False` podczas wpisywania pętli nie Uruchom jeszcze raz.  
  
 `condition` Zazwyczaj wyniki porównania dwóch wartości, ale może być dowolne wyrażenie obliczane do [— typ danych logicznych](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`). Wyrażenie nie może zawierać wartości inny typ danych, takich jak typu liczbowego, który został przekonwertowany na `Boolean`.  
  
 Można zagnieżdżać `While` pętle, umieszczając pętli w innym. Można zagnieżdżać w różnych rodzajów struktury sterujące wewnątrz innych. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Zakończ podczas  
 [Wyjść, gdy](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji można podać inny sposób, aby zakończyć `While` pętli. `Exit While` natychmiast przenosi kontroli do instrukcji następującej `End While` instrukcji.  
  
 Zazwyczaj używają `Exit While` po spełnienia określonego warunku jest obliczane (na przykład w `If...Then...Else` struktury). Możesz zamknąć pętlę Jeśli wykryć warunek, który ułatwia niepotrzebnych lub nie można kontynuować iteracja, takich jak Błędna wartość lub zakończenia żądania. Można użyć `Exit While` podczas testowania dla warunku, który może powodować *nieskończonej pętli*, która jest pętli, które można uruchomić bardzo duże lub nawet nieskończoną liczbę razy. Następnie można użyć `Exit While` wyjścia z pętli.  
  
 Może zawierać dowolną liczbę `Exit While` instrukcje w `While` pętli.  
  
 Gdy jest używany w zagnieżdżonych `While` pętle, `Exit While` przekazuje sterowanie poza najbardziej pętli i do następnego wyższy poziom zagnieżdżenia.  
  
 `Continue While` Instrukcji natychmiast przekazuje sterowanie do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [kontynuować instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli kontynuować do momentu zakończenia `index` zmiennej jest większa niż 10.  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Continue While` i `Exit While` instrukcje.  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. <xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> które odczytuje znaki. W `While` warunku, <xref:System.IO.StreamReader.Peek%2A> metoda `StreamReader` Określa, czy plik zawiera dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Continue, instrukcja](../../../visual-basic/language-reference/statements/continue-statement.md)
