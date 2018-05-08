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
ms.openlocfilehash: e12cdc1ae405b877d4d27d1947c98dcb51938ba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop — Instrukcja (Visual Basic)
Powtarza blok instrukcji podczas `Boolean` warunek jest `True` lub warunek staje się `True`.  
  
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
|`While`|Wymagany, chyba że `Until` jest używany. Powtórz pętli do `condition` jest `False`.|  
|`Until`|Wymagany, chyba że `While` jest używany. Powtórz pętli do `condition` jest `True`.|  
|`condition`|Opcjonalna. `Boolean` Wyrażenie. Jeśli `condition` jest `Nothing`, Visual Basic traktuje ją jako `False`.|  
|`statements`|Opcjonalna. Co najmniej jeden instrukcji, które są powtarzane podczas lub do momentu, `condition` jest `True`.|  
|`Continue Do`|Opcjonalna. Przekazuje sterowanie do następnej iteracji `Do` pętli.|  
|`Exit Do`|Opcjonalna. Przekazuje sterowanie poza `Do` pętli.|  
|`Loop`|Wymagana. Kończy definicję `Do` pętli.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Do...Loop` struktury, gdy ma zostać powtórzony zestaw instrukcji o nieograniczonej liczby godzin, dopóki spełniony jest warunek. Jeśli chcesz powtarzać instrukcje jest określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszym rozwiązaniem.  
  
 Możesz użyć dowolnej `While` lub `Until` do określenia `condition`, ale nie oba.  
  
 Możesz przetestować `condition` tylko jeden raz, na początek lub koniec pętli. W przypadku testowania `condition` na początku pętli (w `Do` instrukcji), pętli nie może uruchomić jeszcze raz. Jeśli test na końcu pętli (w `Loop` instrukcji), pętli jest zawsze uruchamiany co najmniej jeden raz.  
  
 Ten stan jest zazwyczaj wynikiem porównania dwóch wartości, ale może być dowolne wyrażenie obliczane do [— typ danych logicznych](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`). Zawiera ona wartości z innych typów danych, takich jak typy liczbowe, które zostały przekonwertowane na `Boolean`.  
  
 Można zagnieżdżać `Do` pętle, ustawiając dla pętli w innym. Można zagnieżdżać w różnych rodzajów struktury sterujące wewnątrz innych. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  `Do...Loop` Struktura zapewnia większą elastyczność niż [podczas... Instrukcji End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ponieważ umożliwia podjęcie decyzji o zakończenie pętli podczas `condition` przestanie być `True` lub po raz pierwszy staje się `True`. Można również do testowania `condition` na początek lub koniec pętli.  
  
## <a name="exit-do"></a>Czy zakończyć  
 [Zakończyć czy](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji zapewnia alternatywny sposób, aby zakończyć `Do…Loop`. `Exit Do` natychmiast przenosi formantu do instrukcji następującej `Loop` instrukcji.  
  
 `Exit Do` jest często używana po spełnienia określonego warunku jest obliczane, na przykład w `If...Then...Else` struktury. Możesz zamknąć pętlę Jeśli wykryć warunek, który ułatwia niepotrzebnych lub nie można kontynuować iteracja, takich jak Błędna wartość lub zakończenia żądania. Jedno użycie `Exit Do` służy do testowania dla warunku, który może powodować *nieskończonej pętli*, która jest pętli, które można uruchomić dużych lub nawet nieskończoną liczbę razy. Można użyć `Exit Do` wyjścia z pętli.  
  
 Może zawierać dowolną liczbę `Exit Do` instrukcje w `Do…Loop`.  
  
 Gdy jest używany w zagnieżdżonych `Do` pętle, `Exit Do` przekazuje sterowanie poza najbardziej pętli i do następnego wyższy poziom zagnieżdżenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli kontynuować do momentu zakończenia `index` zmiennej jest większa niż 10. `Until` Klauzuli znajduje się na końcu pętli.  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `While` klauzuli zamiast `Until` klauzuli i `condition` został przetestowany na początku pętla, a nie na końcu.  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `condition` zatrzymuje pętli podczas `index` zmiennej jest większa niż 100. `If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcji, aby zatrzymać pętli, gdy zmienna indeksu jest większa niż 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. <xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> które odczytuje znaki. W `Do...Loop` warunku, <xref:System.IO.StreamReader.Peek%2A> metoda `StreamReader` Określa, czy są wszystkie dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
