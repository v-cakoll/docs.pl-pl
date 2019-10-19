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
ms.openlocfilehash: eff5239e07ca27f40ece5af68f46c491be91cf09
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583439"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop — Instrukcja (Visual Basic)
Powtarza blok instrukcji, gdy warunek `Boolean` jest `True` lub do momentu, aż stanie się `True`.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
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
|`Do`|Wymagany. Uruchamia definicję pętli `Do`.|  
|`While`|Wymagane, chyba że zostanie użyta `Until`. Powtarzaj pętlę do momentu `False` `condition`.|  
|`Until`|Wymagane, chyba że zostanie użyta `While`. Powtarzaj pętlę do momentu `True` `condition`.|  
|`condition`|Opcjonalny. wyrażenie `Boolean`. Jeśli `condition` jest `Nothing`, Visual Basic traktuje ją jako `False`.|  
|`statements`|Opcjonalny. Co najmniej jednej instrukcji, która jest powtarzana w czasie lub do, `condition` jest `True`.|  
|`Continue Do`|Opcjonalny. Przenosi formant do następnej iteracji pętli `Do`.|  
|`Exit Do`|Opcjonalny. Przenosi kontrolę z pętli `Do`.|  
|`Loop`|Wymagany. Kończy definicję pętli `Do`.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj struktury `Do...Loop`, gdy chcesz powtarzać zestaw instrukcji przez nieokreśloną liczbę razy, aż warunek zostanie spełniony. Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszy wybór.  
  
 Aby określić `condition`, ale nie oba te elementy, można użyć opcji `While` lub `Until`.  
  
 @No__t_0 można testować tylko raz, na początku lub na końcu pętli. Jeśli testujesz `condition` na początku pętli (w instrukcji `Do`), pętla może nie działać nawet jeden raz. Jeśli testujesz na końcu pętli (w instrukcji `Loop`), pętla zawsze jest uruchamiana co najmniej jeden raz.  
  
 Warunek zazwyczaj wynika z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` lub `False`). Obejmuje to wartości innych typów danych, takich jak typy liczbowe, które zostały przekonwertowane na `Boolean`.  
  
 Pętle `Do` można zagnieżdżać, umieszczając jedną pętlę w innej. Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> Struktura `Do...Loop` zapewnia większą elastyczność niż [while... Instrukcja End while](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , ponieważ umożliwia podjęcie decyzji, czy przerwać pętlę, gdy `condition` przestaje być `True` lub gdy po raz pierwszy stanie się `True`. Umożliwia również przetestowanie `condition` na początku lub na końcu pętli.  
  
## <a name="exit-do"></a>Zakończ działanie  
 Instrukcja [exiter](../../../visual-basic/language-reference/statements/exit-statement.md) może zapewnić alternatywny sposób wyjścia `Do…Loop`. `Exit Do` natychmiast przenosi kontrolę do instrukcji, która następuje po instrukcji `Loop`.  
  
 `Exit Do` jest często używana po ocenie pewnego warunku, na przykład w strukturze `If...Then...Else`. Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia. Jednym z `Exit Do` jest przetestowanie stanu, który może spowodować nieskończoną *pętlę*, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Możesz użyć `Exit Do`, aby wyjść z pętli.  
  
 Możesz dołączyć dowolną liczbę instrukcji `Exit Do` w dowolnym miejscu `Do…Loop`.  
  
 Gdy jest używany w zagnieżdżonych pętlach `Do`, `Exit Do` transferuje kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki zmienna `index` nie będzie większa niż 10. Klauzula `Until` znajduje się na końcu pętli.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest używana klauzula `While` zamiast klauzuli `Until`, a `condition` jest testowana na początku pętli, a nie na końcu.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `condition` przerywa pętlę, gdy zmienna `index` jest większa niż 100. Instrukcja `If` w pętli, jednak powoduje, że instrukcja `Exit Do` przerywa pętlę, gdy zmienna indeksu jest większa niż 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. Metoda <xref:System.IO.File.OpenText%2A> otwiera plik i zwraca <xref:System.IO.StreamReader>, który odczytuje znaki. W warunku `Do...Loop` Metoda <xref:System.IO.StreamReader.Peek%2A> `StreamReader` określa, czy istnieją dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
