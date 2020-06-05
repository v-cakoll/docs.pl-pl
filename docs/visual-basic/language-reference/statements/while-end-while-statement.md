---
title: While...End While, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: d9eb8cb95d46e860aa127954d7b44e37991d4a13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391589"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While — Instrukcja (Visual Basic)
Uruchamia serię instrukcji pod warunkiem, że dany warunek to `True` .  
  
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
|`condition`|Wymagany. `Boolean`wyrażenia. Jeśli `condition` jest `Nothing` , Visual Basic traktuje go jako `False` .|  
|`statements`|Opcjonalny. Co najmniej jednej instrukcji `While` , która jest uruchamiana za każdym razem `condition` `True` .|  
|`Continue While`|Opcjonalny. Przenosi formant do następnej iteracji `While` bloku.|  
|`Exit While`|Opcjonalny. Przenosi kontrolę z `While` bloku.|  
|`End While`|Wymagany. Kończy definicję `While` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `While...End While` struktury, gdy chcesz powtórzyć zestaw instrukcji przez nieokreśloną liczbę razy, tak długo, jak warunek pozostanie nieokreślony `True` . Jeśli potrzebujesz większej elastyczności, w której testować warunek lub wynik, dla którego chcesz go przetestować, możesz preferować do [... Loop — instrukcja](do-loop-statement.md). Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](for-next-statement.md) jest zwykle lepszy wybór.  
  
> [!NOTE]
> `While`Słowo kluczowe jest również używane w. [.. Instrukcja Loop](do-loop-statement.md), [klauzula Skip While](../queries/skip-while-clause.md) i [klauzula Take While](../queries/take-while-clause.md).  
  
 Jeśli `condition` jest `True` , to wszystkie `statements` uruchomienia do momentu `End While` napotkania instrukcji. Następnie formant wraca do `While` instrukcji i `condition` zostanie ponownie sprawdzony. Jeśli `condition` jest nadal `True` , proces jest powtarzany. Jeśli jest `False` , sterowanie przechodzi do instrukcji, która następuje po `End While` instrukcji.  
  
 `While`Instrukcja zawsze sprawdza warunek przed rozpoczęciem pętli. Pętla jest kontynuowana, gdy warunek pozostanie `True` . Jeśli `condition` jest to `False` przy pierwszym wprowadzeniu pętli, nie jest uruchamiane nawet raz.  
  
 `condition`Zazwyczaj wynika to z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../data-types/boolean-data-type.md) ( `True` lub `False` ). To wyrażenie może zawierać wartość innego typu danych, na przykład typ liczbowy, który został przekonwertowany na `Boolean` .  
  
 Pętle można zagnieżdżać `While` , umieszczając jedną pętlę w innej. Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Zakończ, gdy  
 Instrukcja [Exit While](exit-statement.md) może zapewnić inny sposób wykończenia `While` pętli. `Exit While`natychmiast przekazuje sterowanie do instrukcji, która następuje po `End While` instrukcji.  
  
 Zwykle używasz `Exit While` po obliczeniu pewnego warunku (na przykład w `If...Then...Else` strukturze). Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia. Można użyć `Exit While` podczas testu dla warunku, który może spowodować *nieskończoną pętlę*, która jest pętlą, która może uruchamiać bardzo dużą lub nawet nieskończoną liczbę razy. Można następnie użyć, `Exit While` Aby wyjść z pętli.  
  
 Dowolną liczbę instrukcji można umieścić `Exit While` w dowolnym miejscu w `While` pętli.  
  
 W przypadku użycia wewnątrz `While` pętli zagnieżdżonych, program `Exit While` przenosi kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.  
  
 `Continue While`Instrukcja natychmiast przenosi formant do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](continue-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki `index` zmienna nie będzie większa niż 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie `Continue While` `Exit While` instrukcji i.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. <xref:System.IO.File.OpenText%2A>Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> , który odczytuje znaki. W `While` warunku <xref:System.IO.StreamReader.Peek%2A> Metoda `StreamReader` określa, czy plik zawiera dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury pętli](../../programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop, instrukcja](do-loop-statement.md)
- [For...Next, instrukcja](for-next-statement.md)
- [Boolean, typ danych](../data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](exit-statement.md)
- [Continue — instrukcja](continue-statement.md)
