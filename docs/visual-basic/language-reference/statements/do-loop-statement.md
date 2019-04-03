---
title: Do...Loop — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 3ff3d67f38f510b798da3e470de066cff1e98f29
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826044"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop — Instrukcja (Visual Basic)
Powtarza blok instrukcji podczas `Boolean` warunek jest `True` lub dopóki warunek przestaje być `True`.  
  
## <a name="syntax"></a>Składnia  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`Do`|Wymagana. Uruchamia definicji `Do` pętli.|  
|`While`|Wymagane, chyba że `Until` jest używany. Powtórz pętli do `condition` jest `False`.|  
|`Until`|Wymagane, chyba że `While` jest używany. Powtórz pętli do `condition` jest `True`.|  
|`condition`|Opcjonalna. `Boolean` wyrażenie. Jeśli `condition` jest `Nothing`, Visual Basic traktuje je jako `False`.|  
|`statements`|Opcjonalna. Jedna lub więcej instrukcji, które są powtarzane while lub do momentu, `condition` jest `True`.|  
|`Continue Do`|Opcjonalna. Przekazuje sterowanie do następnej iteracji `Do` pętli.|  
|`Exit Do`|Opcjonalna. Przekazuje sterowanie poza `Do` pętli.|  
|`Loop`|Wymagana. Kończy definicję `Do` pętli.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Do...Loop` struktury, gdy chcesz powtórzyć zbiór instrukcji na nieokreśloną liczbę razy, dopóki nie zostanie spełniony jakiś warunek. Jeśli chcesz powtórzyć oświadczeń określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) zazwyczaj jest lepszym rozwiązaniem.  
  
 Można użyć dowolnego `While` lub `Until` do określenia `condition`, ale nie oba jednocześnie.  
  
 Możesz przetestować `condition` tylko jeden raz na początku lub końcu pętli. Jeśli testujesz `condition` przy uruchamianiu pętli (w `Do` instrukcji), pętla nie mogą być uruchamiane jeszcze raz. Jeśli test na końcu pętli (w `Loop` instrukcji), pętla zawsze działa co najmniej jeden raz.  
  
 Warunek jest zazwyczaj wynikiem porównania dwóch wartości, ale może być dowolne wyrażenie, które daje w wyniku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`). Obejmuje to wartości inne typy danych, takich jak typy liczbowe, które zostały przekonwertowane na `Boolean`.  
  
 Można zagnieżdżać `Do` pętli przez umieszczenie pętli w innym. Można także zagnieżdżać różne rodzaje struktur sterujących wewnątrz innych. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  `Do...Loop` Struktura zapewnia większą elastyczność niż [podczas... End While-instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , ponieważ pozwala zdecydować, czy do zakończenia pętli po `condition` przestanie być `True` lub po raz pierwszy staje się `True`. Można również do testowania `condition` na początku lub końcu pętli.  
  
## <a name="exit-do"></a>Zakończ  
 [Należy zamknąć](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji może zapewnić alternatywny sposób, aby zakończyć działanie `Do…Loop`. `Exit Do` natychmiast przekazuje sterowanie do instrukcji następującej `Loop` instrukcji.  
  
 `Exit Do` jest często używana po ocenieniu jakiś warunek, na przykład w `If...Then...Else` struktury. Można zamknąć pętli, jeśli wykryje warunek, który sprawia, że niepotrzebnych lub niemożliwe kontynuować, iteracja, np. Błędna wartość lub żądanie zakończenia działania. Jednym z zastosowań `Exit Do` służy do testowania dla warunku, który może powodować *nieskończoną pętlę*, czyli pętlę, która może działać dużych lub nawet nieskończona liczba prób. Możesz użyć `Exit Do` jako znak ucieczki dla pętli.  
  
 Może zawierać dowolną liczbę `Exit Do` instrukcji w `Do…Loop`.  
  
 Gdy jest używana w ramach zagnieżdżonych `Do` pętli, `Exit Do` przenosi sterowanie na dostęp do najaktualniejszych najbardziej wewnętrznej i do następnego wyższy poziom zagnieżdżenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli nadal działać do momentu `index` zmiennej jest większa niż 10. `Until` Klauzula jest na końcu pętli.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `While` klauzuli zamiast `Until` klauzuli i `condition` jest testowany na początku pętli, zamiast na końcu.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `condition` pętla zatrzymuje się podczas `index` zmiennej jest większa niż 100. `If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcję, aby zatrzymanie pętli, gdy zmienna index jest większy niż 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. <xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> , odczytuje znaki. W `Do...Loop` warunku <xref:System.IO.StreamReader.Peek%2A> metody `StreamReader` Określa, czy istnieją dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
