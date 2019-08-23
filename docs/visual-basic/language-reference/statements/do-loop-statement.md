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
ms.openlocfilehash: 75a2129a9f332024831d97021e381f1b3d4fa048
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942996"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop — Instrukcja (Visual Basic)
Powtarza blok instrukcji, gdy `Boolean` warunek jest `True` lub do momentu, aż stanie się `True`.  
  
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
|`Do`|Wymagane. Uruchamia definicję `Do` pętli.|  
|`While`|Wymagane, `Until` chyba że jest używany. Powtarzaj pętlę `condition` do `False`.|  
|`Until`|Wymagane, `While` chyba że jest używany. Powtarzaj pętlę `condition` do `True`.|  
|`condition`|Opcjonalna. `Boolean`wyrażenia. Jeśli `condition` `False`jest `Nothing`, Visual Basic traktuje go jako.|  
|`statements`|Opcjonalny. Co najmniej jedna instrukcja, która jest powtarzana w czasie lub `condition` do `True`, jest.|  
|`Continue Do`|Opcjonalny. Przenosi formant do następnej iteracji `Do` pętli.|  
|`Exit Do`|Opcjonalna. Przenosi kontrolę z `Do` pętli.|  
|`Loop`|Wymagany. Kończy definicję `Do` pętli.|  
  
## <a name="remarks"></a>Uwagi  
 `Do...Loop` Użyj struktury, gdy chcesz powtórzyć zestaw instrukcji przez nieokreśloną liczbę razy, aż warunek zostanie spełniony. Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszy wybór.  
  
 Możesz użyć albo `While` `Until` , aby określić `condition`, ale nie oba jednocześnie.  
  
 Można testować `condition` tylko jeden raz, na początku lub na końcu pętli. Jeśli testujesz `condition` na początku pętli ( `Do` w instrukcji), pętla może nie działać nawet jeden raz. Jeśli testujesz na końcu pętli (w `Loop` instrukcji), pętla zawsze jest uruchamiana co najmniej jeden raz.  
  
 Warunek zazwyczaj wynika z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` lub `False`). Obejmuje to wartości innych typów danych, takich jak typy liczbowe, które zostały przekonwertowane na `Boolean`.  
  
 Pętle można `Do` zagnieżdżać, umieszczając jedną pętlę w innej. Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `Do...Loop` Struktura zapewnia większą elastyczność niż [while... Instrukcja End while](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , ponieważ umożliwia podjęcie decyzji, czy przerwać pętlę, `condition` gdy zostanie `True` ona zatrzymana `True`. Umożliwia również przetestowanie `condition` na początku lub na końcu pętli.  
  
## <a name="exit-do"></a>Zakończ działanie  
 Instrukcja [exiter](../../../visual-basic/language-reference/statements/exit-statement.md) może zapewnić alternatywny sposób wyjścia `Do…Loop`. `Exit Do`natychmiast przenosi kontrolę do instrukcji, która następuje po `Loop` instrukcji.  
  
 `Exit Do`jest często używany po ocenie pewnego warunku, na przykład w `If...Then...Else` strukturze. Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia. Jednym z `Exit Do` nich jest przetestowanie stanu, który może spowodować nieskończoną *pętlę*, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Możesz użyć `Exit Do` , aby wyjść z pętli.  
  
 Możesz dołączyć dowolną liczbę `Exit Do` instrukcji `Do…Loop`w dowolnym miejscu.  
  
 W przypadku użycia wewnątrz `Do` pętli zagnieżdżonych, program `Exit Do` przenosi kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki `index` zmienna nie będzie większa niż 10. `Until` Klauzula znajduje się na końcu pętli.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest używana `While` klauzula zamiast `Until` klauzuli i `condition` jest testowana na początku pętli, a nie na końcu.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, zatrzymanie `condition` pętli, `index` gdy zmienna jest większa niż 100. Instrukcja w pętli, jednak `Exit Do` powoduje zatrzymanie pętli, gdy zmienna indeksu jest większa niż 10. `If`  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. Metoda otwiera plik i <xref:System.IO.StreamReader> zwraca, który odczytuje znaki. <xref:System.IO.File.OpenText%2A> W warunku <xref:System.IO.StreamReader.Peek%2A> Metoda`StreamReader` określa, czy istnieją dodatkowe znaki. `Do...Loop`  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
