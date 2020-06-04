---
title: Do...Loop, instrukcja
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
ms.openlocfilehash: a9ec6caccbe161a39b592a642a938b81bae911a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404787"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop — Instrukcja (Visual Basic)
Powtarza blok instrukcji, gdy `Boolean` warunek jest `True` lub do momentu, aż stanie się `True` .  
  
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
|`Do`|Wymagany. Uruchamia definicję `Do` pętli.|  
|`While`|Wymagane, chyba że `Until` jest używany. Powtarzaj pętlę `condition` do `False` .|  
|`Until`|Wymagane, chyba że `While` jest używany. Powtarzaj pętlę `condition` do `True` .|  
|`condition`|Opcjonalny. `Boolean`wyrażenia. Jeśli `condition` jest `Nothing` , Visual Basic traktuje go jako `False` .|  
|`statements`|Opcjonalny. Co najmniej jedna instrukcja, która jest powtarzana w czasie lub do, `condition` jest `True` .|  
|`Continue Do`|Opcjonalny. Przenosi formant do następnej iteracji `Do` pętli.|  
|`Exit Do`|Opcjonalny. Przenosi kontrolę z `Do` pętli.|  
|`Loop`|Wymagany. Kończy definicję `Do` pętli.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Do...Loop` struktury, gdy chcesz powtórzyć zestaw instrukcji przez nieokreśloną liczbę razy, aż warunek zostanie spełniony. Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](for-next-statement.md) jest zwykle lepszy wybór.  
  
 Możesz użyć albo `While` `Until` , aby określić `condition` , ale nie oba jednocześnie.  
  
 Można testować `condition` tylko jeden raz, na początku lub na końcu pętli. Jeśli testujesz `condition` na początku pętli (w `Do` instrukcji), pętla może nie działać nawet jeden raz. Jeśli testujesz na końcu pętli (w `Loop` instrukcji), pętla zawsze jest uruchamiana co najmniej jeden raz.  
  
 Warunek zazwyczaj wynika z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../data-types/boolean-data-type.md) ( `True` lub `False` ). Obejmuje to wartości innych typów danych, takich jak typy liczbowe, które zostały przekonwertowane na `Boolean` .  
  
 Pętle można zagnieżdżać `Do` , umieszczając jedną pętlę w innej. Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> `Do...Loop`Struktura zapewnia większą elastyczność niż [while... Instrukcja End while](while-end-while-statement.md) , ponieważ umożliwia podjęcie decyzji, czy przerwać pętlę, gdy zostanie ona `condition` zatrzymana `True` `True` . Umożliwia również przetestowanie `condition` na początku lub na końcu pętli.  
  
## <a name="exit-do"></a>Zakończ działanie  
 Instrukcja [exiter](exit-statement.md) może zapewnić alternatywny sposób wyjścia `Do…Loop` . `Exit Do`natychmiast przenosi kontrolę do instrukcji, która następuje po `Loop` instrukcji.  
  
 `Exit Do`jest często używany po ocenie pewnego warunku, na przykład w `If...Then...Else` strukturze. Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia. Jednym z nich `Exit Do` jest przetestowanie stanu, który może spowodować nieskończoną *pętlę*, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Możesz użyć, `Exit Do` Aby wyjść z pętli.  
  
 Możesz dołączyć dowolną liczbę `Exit Do` instrukcji w dowolnym miejscu `Do…Loop` .  
  
 W przypadku użycia wewnątrz `Do` pętli zagnieżdżonych, program `Exit Do` przenosi kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki `index` zmienna nie będzie większa niż 10. `Until`Klauzula znajduje się na końcu pętli.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest używana `While` klauzula zamiast `Until` klauzuli i `condition` jest testowana na początku pętli, a nie na końcu.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, `condition` zatrzymanie pętli, gdy `index` zmienna jest większa niż 100. `If`Instrukcja w pętli, jednak powoduje `Exit Do` zatrzymanie pętli, gdy zmienna indeksu jest większa niż 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym. <xref:System.IO.File.OpenText%2A>Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> , który odczytuje znaki. W `Do...Loop` warunku <xref:System.IO.StreamReader.Peek%2A> Metoda określa, czy istnieją `StreamReader` dodatkowe znaki.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury pętli](../../programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next, instrukcja](for-next-statement.md)
- [Boolean, typ danych](../data-types/boolean-data-type.md)
- [Zagnieżdżone struktury sterujące](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](exit-statement.md)
- [While...End While, instrukcja](while-end-while-statement.md)
