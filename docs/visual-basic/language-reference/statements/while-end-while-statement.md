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
ms.openlocfilehash: 5da05835998b2e9ef9aeefe5b00faf9e1ecb9ce2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582268"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While — Instrukcja (Visual Basic)
Uruchamia serię instrukcji pod warunkiem, że dany warunek jest `True`.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
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
|`condition`|Wymagany. wyrażenie `Boolean`. Jeśli `condition` jest `Nothing`, Visual Basic traktuje ją jako `False`.|  
|`statements`|Opcjonalny. Co najmniej jedna instrukcja `While`, która jest uruchamiana za każdym razem, gdy `condition` jest `True`.|  
|`Continue While`|Opcjonalny. Przenosi formant do następnej iteracji bloku `While`.|  
|`Exit While`|Opcjonalny. Przenosi kontrolę z bloku `While`.|  
|`End While`|Wymagany. Kończy definicję bloku `While`.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj struktury `While...End While`, gdy chcesz powtórzyć zestaw instrukcji przez nieokreśloną liczbę razy, tak długo, jak warunek pozostanie `True`. Jeśli potrzebujesz większej elastyczności, w której testować warunek lub wynik, dla którego chcesz go przetestować, możesz preferować do [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md). Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszy wybór.  
  
> [!NOTE]
> Słowo kluczowe `While` jest również używane w. [.. Instrukcja Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), [klauzula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [klauzula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Jeśli `condition` jest `True`, wszystkie `statements` uruchamiane do momentu napotkania instrukcji `End While`. Następnie formant wraca do instrukcji `While` i ponownie sprawdzane `condition`. Jeśli `condition` nadal jest `True`, proces jest powtarzany. Jeśli jest `False`, sterowanie przechodzi do instrukcji, która następuje po instrukcji `End While`.  
  
 Instrukcja `While` zawsze sprawdza warunek przed rozpoczęciem pętli. Zapętlenie jest kontynuowane, gdy warunek pozostanie `True`. Jeśli `condition` jest `False`, gdy po raz pierwszy wprowadzisz pętlę, nie zostanie ona uruchomiona nawet raz.  
  
 @No__t_0 zwykle wynika z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` lub `False`). To wyrażenie może zawierać wartość innego typu danych, na przykład typ liczbowy, który został przekonwertowany na `Boolean`.  
  
 Pętle `While` można zagnieżdżać, umieszczając jedną pętlę w innej. Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Zakończ, gdy  
 Instrukcja [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) może zapewnić inny sposób, aby zakończyć pętlę `While`. `Exit While` natychmiast przenosi kontrolę do instrukcji, która następuje po instrukcji `End While`.  
  
 Zazwyczaj używa się `Exit While` po obliczeniu pewnego warunku (na przykład w strukturze `If...Then...Else`). Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia. @No__t_0 można użyć podczas testowania dla warunku, który może spowodować nieskończoną *pętlę*, która jest pętlą, która może uruchamiać bardzo dużą lub nawet nieskończoną liczbę razy. Następnie można użyć `Exit While` do ucieczki pętli.  
  
 Dowolną liczbę instrukcji `Exit While` można umieścić w dowolnym miejscu w pętli `While`.  
  
 Gdy jest używany w zagnieżdżonych pętlach `While`, `Exit While` transferuje kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.  
  
 Instrukcja `Continue While` natychmiast przenosi formant do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki zmienna `index` nie będzie większa niż 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie instrukcji `Continue While` i `Exit While`.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. Metoda <xref:System.IO.File.OpenText%2A> otwiera plik i zwraca <xref:System.IO.StreamReader>, który odczytuje znaki. W warunku `While` Metoda <xref:System.IO.StreamReader.Peek%2A> `StreamReader` określa, czy plik zawiera dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue, instrukcja](../../../visual-basic/language-reference/statements/continue-statement.md)
