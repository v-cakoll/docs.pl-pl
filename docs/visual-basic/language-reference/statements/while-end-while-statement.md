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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965809"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While — Instrukcja (Visual Basic)
Uruchamia serię instrukcji pod warunkiem, że dany warunek to `True`.  
  
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
|`condition`|Wymagana. `Boolean`wyrażenia. Jeśli `condition` `False`jest `Nothing`, Visual Basic traktuje go jako.|  
|`statements`|Opcjonalny. Co najmniej jednej instrukcji `While`, która jest `True`uruchamiana za `condition` każdym razem.|  
|`Continue While`|Opcjonalny. Przenosi formant do następnej iteracji `While` bloku.|  
|`Exit While`|Opcjonalny. Przenosi kontrolę z `While` bloku.|  
|`End While`|Wymagana. Kończy definicję `While` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj struktury, gdy chcesz powtórzyć zestaw instrukcji przez nieokreśloną liczbę razy, tak długo, jak warunek pozostanie `True`nieokreślony. `While...End While` Jeśli potrzebujesz większej elastyczności, w której testować warunek lub wynik, dla którego chcesz go przetestować, możesz preferować do [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md). Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszy wybór.  
  
> [!NOTE]
> `While` Słowo kluczowe jest również używane w. [.. Instrukcja Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), [klauzula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [klauzula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Jeśli `condition` `statements` `End While` jest `True`, to wszystkie uruchomienia do momentu napotkania instrukcji. Następnie formant wraca do `While` instrukcji i `condition` zostanie ponownie sprawdzony. Jeśli `condition` jest nadal `True`, proces jest powtarzany. Jeśli jest `False`, sterowanie przechodzi do instrukcji, która następuje po `End While` instrukcji.  
  
 `While` Instrukcja zawsze sprawdza warunek przed rozpoczęciem pętli. Pętla jest kontynuowana, gdy `True`warunek pozostanie. Jeśli `condition` jest `False` to przy pierwszym wprowadzeniu pętli, nie jest uruchamiane nawet raz.  
  
 Zazwyczaj wynika to z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` lub `False`). `condition` To wyrażenie może zawierać wartość innego typu danych, na przykład typ liczbowy, który został przekonwertowany na `Boolean`.  
  
 Pętle można `While` zagnieżdżać, umieszczając jedną pętlę w innej. Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Zakończ, gdy  
 Instrukcja [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) może zapewnić inny sposób wykończenia `While` pętli. `Exit While`natychmiast przekazuje sterowanie do instrukcji, która następuje po `End While` instrukcji.  
  
 Zwykle używasz `Exit While` po obliczeniu pewnego warunku (na przykład `If...Then...Else` w strukturze). Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia. Można użyć `Exit While` podczas testu dla warunku, który może spowodować nieskończoną *pętlę*, która jest pętlą, która może uruchamiać bardzo dużą lub nawet nieskończoną liczbę razy. Można następnie użyć `Exit While` , aby wyjść z pętli.  
  
 Dowolną liczbę `Exit While` instrukcji można umieścić `While` w dowolnym miejscu w pętli.  
  
 W przypadku użycia wewnątrz `While` pętli zagnieżdżonych, program `Exit While` przenosi kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.  
  
 `Continue While` Instrukcja natychmiast przenosi formant do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki `index` zmienna nie będzie większa niż 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie `Continue While` instrukcji i. `Exit While`  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. Metoda otwiera plik i <xref:System.IO.StreamReader> zwraca, który odczytuje znaki. <xref:System.IO.File.OpenText%2A> W warunku <xref:System.IO.StreamReader.Peek%2A> Metoda`StreamReader` określa, czy plik zawiera dodatkowe znaki. `While`  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue, instrukcja](../../../visual-basic/language-reference/statements/continue-statement.md)
