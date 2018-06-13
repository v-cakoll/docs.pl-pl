---
title: For...Next — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 8c54189499b7d5b52cf93b4a0ae6cc47356bf57e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605332"
---
# <a name="fornext-statement-visual-basic"></a>For...Next — Instrukcja (Visual Basic)
Powtarza określoną liczbę razy grupę instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>Części  
  
|Część|Opis|  
|----------|-----------------|  
|`counter`|Wymagane w `For` instrukcji. Zmienna numeryczna. Zmienna sterująca pętli. Aby uzyskać więcej informacji, zobacz [Argument licznika](#BKMK_Counter) dalszej części tego tematu.|  
|`datatype`|Opcjonalna. Typ danych `counter`. Aby uzyskać więcej informacji, zobacz [Argument licznika](#BKMK_Counter) dalszej części tego tematu.|  
|`start`|Wymagana. Wyrażenie liczbowe. Początkowa wartość `counter`.|  
|`end`|Wymagana. Wyrażenie liczbowe. Końcowa wartość `counter`.|  
|`step`|Opcjonalna. Wyrażenie liczbowe. Wartość, o którą `counter` jest zwiększany po każdej za pomocą pętli.|  
|`statements`|Opcjonalna. Co najmniej jeden instrukcji między `For` i `Next` uruchomioną określoną liczbę razy.|  
|`Continue For`|Opcjonalna. Transfer kontroli do następnej iteracji pętli.|  
|`Exit For`|Opcjonalna. Przekazuje sterowanie poza `For` pętli.|  
|`Next`|Wymagana. Kończy definicję `For` pętli.|  
  
> [!NOTE]
>  `To` Słowo kluczowe jest używane w tej instrukcji, aby określić zakres licznika. Można również użyć słowa kluczowego w [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md) w deklaracje tablicy. Aby uzyskać więcej informacji na temat deklaracje tablicy, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Proste przykłady  
 Możesz użyć `For`... `Next` struktury, gdy ma zostać powtórzony zestaw instrukcji określoną liczbę razy.  
  
 W poniższym przykładzie `index` zmiennej rozpoczyna się od wartości 1 i jest zwiększany przy każdej iteracji pętli kończące się po wartości `index` osiągnie 5.  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 W poniższym przykładzie `number` zmiennej rozpoczyna się od 2 i zostanie zmniejszona 0,25 w każdej iteracji pętli kończące się po wartości `number` wynosić 0. `Step` Argument `-.25` zmniejsza wartość o 0,25 w każdej iteracji pętli.  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  A [podczas... End While — instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md) lub [czy... Instrukcji pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md) działa dobrze, jeśli nie wiadomo, wcześniej ile razy, aby uruchomić instrukcje w pętli. Jednak jeśli oczekujesz do uruchamiania w pętli określoną liczbę razy, `For`... `Next` pętla jest lepszym rozwiązaniem. Liczba iteracji jest określania, kiedy użytkownik wprowadzi pętli.  
  
## <a name="nesting-loops"></a>Zagnieżdżania pętle  
 Można zagnieżdżać `For` pętle, ustawiając dla pętli w innym. W poniższym przykładzie pokazano zagnieżdżonych `For`... `Next` struktur, które mają krok różnych wartości. Zewnętrzne pętli tworzy ciąg dla każdej iteracji pętli. Wewnętrzny pętla zmniejsza zmiennej licznika pętli dla każdej iteracji pętli.  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 Podczas zagnieżdżania pętle, każdej pętli musi mieć unikatową `counter` zmiennej.  
  
 Struktury sterujące różnych rodzajów wewnątrz innych można zagnieżdżać. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Zakończ dla i Kontynuuj dla  
 `Exit For` Instrukcji natychmiast kończy pracę `For`...`Next` pętli i transfer kontroli do instrukcji następującej `Next` instrukcji.  
  
 `Continue For` Instrukcji sterowania natychmiast przenosi do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [kontynuować instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Poniższy przykład przedstawia użycie `Continue For` i `Exit For` instrukcje.  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 Można wprowadzić dowolną liczbę `Exit For` instrukcje w `For`...`Next` pętli. Gdy jest używany w zagnieżdżonych `For`...`Next` pętle, `Exit For` kończy tryb pętli najbardziej i przekazuje sterowanie do następnego wyższego poziomu zagnieżdżenia.  
  
 `Exit For` jest często używana po przeprowadzeniu oceny spełnienia określonego warunku (na przykład w `If`... `Then`... `Else` struktury). Możesz chcieć użyć `Exit For` następujące warunki:  
  
-   Kontynuowanie wykonania iteracji jest niepotrzebne lub niemożliwe. Błędna wartość lub żądanie zakończenia może utworzenia tego warunku.  
  
-   A `Try`... `Catch`... `Finally` wyjątek zostanie przechwycony instrukcji. Można na przykład `Exit For` na końcu `Finally` bloku.  
  
-   Masz nieskończonej pętli, czyli pętli, które można uruchomić dużych lub nawet nieskończoną liczbę razy. W przypadku wykrycia takim stanie, można użyć `Exit For` wyjścia z pętli. Aby uzyskać więcej informacji, zobacz [czy... Pętla instrukcji](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Gdy `For`... `Next` rozpoczyna pętli, ocenia Visual Basic `start`, `end`, i `step`. Visual Basic ocenia te wartości tylko w tym czasie, a następnie przypisuje `start` do `counter`. Przed rozpoczęciem instrukcji uruchamia blok, porównuje Visual Basic `counter` do `end`. Jeśli `counter` już jest większy niż `end` wartości (lub mniejszy, jeśli `step` jest ujemna), `For` kończy się w pętli i kontrola przechodzi do instrukcji następującej `Next` instrukcji. W przeciwnym razie uruchamia blok instrukcji.  
  
 Po każdej aktualizacji Visual Basic napotka `Next` instrukcji, zwiększa `counter` przez `step` , przywracając `For` instrukcji. Ponownie porównuje `counter` do `end`, i ponownie go uruchamia blok albo kończy tryb pętli, w zależności od wyniku. Ten proces jest kontynuowany do momentu `counter` przekazuje `end` lub `Exit For` napotkano instrukcji.  
  
 Pętla nie zatrzymania do momentu `counter` minął `end`. Jeśli `counter` jest równa `end`, pętla będzie kontynuowane. Porównanie, która określa, czy do uruchomienia bloku jest `counter`  <=  `end` Jeśli `step` jest dodatnia i `counter`  >=  `end` Jeśli `step` jest ujemna.  
  
 W przypadku zmiany wartości `counter` znajduje się wewnątrz pętli, może być trudne do odczytu i debugowania kodu. Zmiana wartości `start`, `end`, lub `step` nie ma wpływu na wartości iteracji, które zostały uznane za najpierw wprowadzenie pętli.  
  
 Jeśli zagnieździć pętle, kompilator sygnalizuje błąd, jeśli wystąpi `Next` instrukcji zewnętrzne poziom zagnieżdżenia przed `Next` instrukcji wewnętrzny poziom. Jednak kompilator wykryć nakładających się błędu tylko w przypadku określenia `counter` w każdym `Next` instrukcji.  
  
### <a name="step-argument"></a>Argument kroku  
 Wartość `step` może być liczbą dodatnią lub ujemną. Ten parametr określa przetwarzanie pętli zgodnie z poniższą tabelą:  
  
|**Wartość kroku**|**Wykonuje pętlę, jeśli**|  
|--------------------|--------------------------|  
|Dodatnia lub równa zero|`counter` <= `end`|  
|Ujemne|`counter` >= `end`|  
  
 Wartość domyślna `step` 1.  
  
###  <a name="BKMK_Counter"></a> Argument licznika  
 W poniższej tabeli przedstawiono czy `counter` definiuje nowej zmiennej lokalnej, która ma zakres do całej `For…Next` pętli. To jest zależny od tego, czy `datatype` istnieje i czy `counter` jest już zdefiniowany.  
  
|Jest `datatype` obecny?|Jest `counter` już zdefiniowane?|Wynik (czy `counter` definiuje nowej zmiennej lokalnej, która ma zakres do całej `For...Next` pętli)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Nie|Tak|Nie, ponieważ `counter` jest już zdefiniowany. Jeśli zakres `counter` nie jest lokalny do procedury występuje ostrzeżenie kompilacji.|  
|Nie|Nie|Tak. Typ danych jest wywnioskowany na podstawie `start`, `end`, i `step` wyrażenia. Aby uzyskać informacje o wnioskowanie o typie, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Tak|Tak|Tak, ale tylko wtedy, gdy istniejące `counter` zmiennej jest zdefiniowany poza procedurą. Tej zmiennej pozostaje oddzielnym. Jeśli zakres istniejących `counter` zmiennej jest lokalny dla procedury, występuje błąd kompilacji.|  
|Tak|Nie|Tak.|  
  
 Typ danych miary `counter` Określa typ iteracji, który musi być jednym z następujących typów:  
  
-   A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, lub `Double`.  
  
-   Wyliczenie zadeklarować przy użyciu [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   `Object`.  
  
-   Typ `T` mający następujących operatorów, gdzie `B` jest typem, który może być używana w `Boolean` wyrażenia.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Opcjonalnie można określić `counter` zmiennej w `Next` instrukcji. Ta składnia poprawia czytelność programu, zwłaszcza, jeśli można zagnieżdżać `For` pętli. Należy określić zmiennej, która jest wyświetlana w polu `For` instrukcji.  
  
 `start`, `end`, I `step` wyrażenia może służyć do oceny do dowolnego typu danych rozszerzająca do typu `counter`. Jeśli używasz typ zdefiniowany przez użytkownika `counter`, może być konieczne zdefiniowanie `CType` operatora konwersji do konwersji typów `start`, `end`, lub `step` do typu `counter`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia usunięcie wszystkich elementów z listy ogólnej. Zamiast [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md), w przykładzie `For`... `Next` instrukcji, która wykonuje iterację w kolejności malejącej. W przykładzie użyto ta technika, ponieważ `removeAt` metoda powoduje elementów po elemencie usunięto mieć niższe wartości indeksu.  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład iteruje wyliczenie zadeklarowana przy użyciu [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie parametrów instrukcji, użyj klasy, która ma przeciążeń operatora dla `+`, `-`, `>=`, i `<=` operatorów.  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic.List%601>  
 [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Kolekcje](../../programming-guide/concepts/collections.md)
