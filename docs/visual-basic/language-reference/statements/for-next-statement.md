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
ms.openlocfilehash: 9a9aed51f6d7bf3233e6e89116b8209b22f3d15d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912417"
---
# <a name="fornext-statement-visual-basic"></a>For...Next — Instrukcja (Visual Basic)
Powtarza grupę instrukcji określoną liczbę razy.  
  
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
  
|Części|Opis|  
|----------|-----------------|  
|`counter`|Wymagane w `For` instrukcji. Zmienna numeryczna. Zmienna sterująca pętli. Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.|  
|`datatype`|Opcjonalna. Typ `counter`danych. Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.|  
|`start`|Wymagany. Wyrażenie liczbowe. Wartość `counter`początkowa.|  
|`end`|Wymagana. Wyrażenie liczbowe. Końcowa wartość parametru `counter`.|  
|`step`|Opcjonalny. Wyrażenie liczbowe. Wartość, według której `counter` jest zwiększana za każdym razem przez pętlę.|  
|`statements`|Opcjonalny. Co najmniej jedna instrukcja między `For` i `Next` , która uruchamia określoną liczbę razy.|  
|`Continue For`|Opcjonalna. Przenosi formant do następnej iteracji pętli.|  
|`Exit For`|Opcjonalny. Przenosi kontrolę z `For` pętli.|  
|`Next`|Wymagany. Kończy definicję `For` pętli.|  
  
> [!NOTE]
> `To` Słowo kluczowe jest używane w tej instrukcji, aby określić zakres dla licznika. Można również użyć słowa kluczowego [SELECT... Instrukcja Case](../../../visual-basic/language-reference/statements/select-case-statement.md) i w deklaracjach tablicowych. Aby uzyskać więcej informacji na temat deklaracji tablicowych, zobacz [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Proste przykłady  
 `For`Używasz... `Next` struktura, w której chcesz powtórzyć zestaw instrukcji przez określoną liczbę razy.  
  
 W poniższym przykładzie `index` zmienna rozpoczyna się od wartości 1 i zwiększa się wraz z każdą iteracją pętli, kończąc po `index` wartości osiągnie 5.  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 W poniższym przykładzie `number` zmienna zaczyna się od 2 i jest zmniejszana o 0,25 dla każdej iteracji pętli, kończąc po `number` wartości osiągnie 0. `Step` Argumentzmniejszawartośćo0,25`-.25` dla każdej iteracji pętli.  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  A [while... Instrukcja End while](../../../visual-basic/language-reference/statements/while-end-while-statement.md) lub [... Instrukcja Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) działa prawidłowo, gdy nie wiadomo, ile razy należy uruchomić instrukcje w pętli. Jeśli jednak oczekuje się, że pętla zostanie uruchomiona określoną liczbę razy, a `For`... `Next` pętla jest lepszym wyborem. Należy określić liczbę iteracji podczas pierwszego wprowadzania pętli.  
  
## <a name="nesting-loops"></a>Pętle zagnieżdżania  
 Pętle można `For` zagnieżdżać, umieszczając jedną pętlę w innej. W poniższym przykładzie pokazano zagnieżdżonych `For`... `Next` struktury, które mają różne wartości kroków. Pętla zewnętrzna tworzy ciąg dla każdej iteracji pętli. Pętla wewnętrzna zmniejsza zmienną licznika pętli dla każdej iteracji pętli.  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 Podczas zagnieżdżania pętli Każda pętla musi mieć unikatową `counter` zmienną.  
  
 Można również zagnieżdżać różne struktury kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Zamknij i Kontynuuj dla  
 Instrukcja natychmiast opuszcza `For`... `Exit For``Next` Pętla i przeniesie sterowanie do instrukcji, która `Next` następuje po instrukcji.  
  
 `Continue For` Instrukcja natychmiast przenosi kontrolę do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Poniższy przykład ilustruje użycie `Continue For` instrukcji i. `Exit For`  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 Można umieścić dowolną liczbę `Exit For` instrukcji `For`w...`Next` for. Używany w zagnieżdżonych `For`...`Next` pętle `Exit For` , opuszcza wewnętrzna pętla i przenosi formant na następny wyższy poziom zagnieżdżenia.  
  
 `Exit For`jest często używany po dokonaniu oszacowania pewnego warunku (na przykład w `If`... `Then`... `Else` struktura). Może być konieczne użycie `Exit For` następujących warunków:  
  
- Kontynuowanie iteracji jest niepotrzebne lub niemożliwe. Wartość błędna lub żądanie zakończenia może stworzyć ten warunek.  
  
- A `Try`... `Catch`... `Finally` instrukcja przechwytuje wyjątek. Możesz użyć `Exit For` na końcu `Finally` bloku.  
  
- Masz nieskończoną pętlę, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Jeśli wykryjesz taki warunek, możesz użyć `Exit For` , aby wyjść z pętli. Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 `For`Gdy... zaczyna się pętla, Visual Basic `start`oblicza `end`,, `step`i. `Next` Visual Basic oblicza te wartości tylko w tym momencie, a następnie `start` przypisuje `counter`do. Przed uruchomieniem bloku instrukcji Visual Basic porównuje `counter` z `end`. Jeśli `counter` jest już większa `end` niż wartość (lub mniejsza, jeśli `step` jest ujemna), `For` pętla kończy się i kontrola przechodzi do instrukcji, która następuje `Next` po instrukcji. W przeciwnym razie blok instrukcji zostanie uruchomiony.  
  
 Za każdym razem, gdy Visual Basic `Next` napotkają instrukcję `step` , zwiększasięprzeziwracadoinstrukcji.`For` `counter` Ponownie porównuje `counter` z `end`, a następnie uruchamia blok lub zamyka pętlę, w zależności od wyniku. Ten proces jest kontynuowany `end` do momentu `counter` przełączenia lub `Exit For` wykonania instrukcji.  
  
 Pętla nie jest zatrzymywana do `end`momentu `counter` przełączenia. Jeśli `counter` jest`end`równe, pętla kontynuuje działanie. Porównanie, które określa, czy ma być uruchamiany blok `counter` , `step` ma  >=  `end` `counter`  <=  `end` wartość dodatnią `step` , a jeśli jest ujemna.  
  
 Jeśli zmienisz wartość `counter` while wewnątrz pętli, kod może być trudniejszy do odczytania i debugowania. Zmiana wartości `start`, `end`lub `step` nie wpływa na wartości iteracji, które zostały określone podczas pierwszego wprowadzenia pętli.  
  
 Jeśli zagnieżdżasz pętle, kompilator sygnalizuje błąd, jeśli napotka `Next` instrukcję na zewnętrznym poziomie zagnieżdżenia `Next` przed instrukcją wewnętrznego poziomu. Jednak kompilator może wykryć ten błąd nakładający się tylko wtedy, gdy określisz `counter` w każdej `Next` instrukcji.  
  
### <a name="step-argument"></a>Argument kroku  
 Wartość `step` może być dodatnia lub ujemna. Ten parametr określa przetwarzanie pętli zgodnie z poniższą tabelą:  
  
|**Wartość kroku**|**Pętla jest wykonywana, jeśli**|  
|--------------------|--------------------------|  
|Wartość dodatnia lub zero|`counter` <= `end`|  
|Ujemne|`counter` >= `end`|  
  
 Wartość `step` domyślna to 1.  
  
### <a name="BKMK_Counter"></a>Argument licznika  
 Poniższa tabela wskazuje, `counter` czy definiuje nową zmienną lokalną, która jest objęta zakresem `For…Next` całej pętli. To określenie zależy od tego, `datatype` czy jest obecne i `counter` czy jest już zdefiniowane.  
  
|Czy `datatype` istnieje?|Czy `counter` jest już zdefiniowany?|Wynik (czy `counter` definiuje nową zmienną lokalną, która jest objęta zakresem całej `For...Next` pętli)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Nie|Tak|Nie, ponieważ `counter` jest już zdefiniowany. Jeśli zakres `counter` nie jest lokalny dla procedury, występuje ostrzeżenie w czasie kompilacji.|  
|Nie|Nie|Tak. Typ danych jest wywnioskowany na podstawie `start`wyrażeń, `end`i. `step` Aby uzyskać informacje na temat wnioskowania o typie, zobacz [instrukcja SELECT](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie typu lokalnego](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Tak|Tak|Tak, ale tylko wtedy, gdy `counter` istniejąca zmienna jest zdefiniowana poza procedurą. Ta zmienna pozostaje oddzielona. Jeśli zakres istniejącej `counter` zmiennej jest lokalny dla procedury, wystąpi błąd w czasie kompilacji.|  
|Tak|Nie|Tak.|  
  
 Typ `counter` danych określa typ iteracji, który musi być jednym z następujących typów:  
  
- A `Byte`, `SByte`, ,`UShort` ,,`Decimal`, ,`ULong`,, lub`Double`. `Short` `UInteger` `Integer` `Long` `Single`  
  
- Wyliczenie zadeklarowane za pomocą [instrukcji enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
- A `Object`.  
  
- Typ `T` , który ma następujące operatory, gdzie `B` jest typem, który `Boolean` może być używany w wyrażeniu.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Opcjonalnie możesz określić `counter` zmienną `Next` w instrukcji. Ta składnia zwiększa czytelność programu, zwłaszcza jeśli istnieją zagnieżdżone `For` pętle. Należy określić zmienną, która pojawia się w odpowiedniej `For` instrukcji.  
  
 Wyrażenia `start` `counter`, `end`i mogąbyćocenianedodowolnegotypudanych,któryjestrozszerzanydotypu.`step` Jeśli używasz `counter`typu zdefiniowanego przez użytkownika dla, może być konieczne `CType` zdefiniowanie operatora konwersji, `start`aby przekonwertować typy, `end`lub `step` na typ `counter`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa wszystkie elementy z listy ogólnej. Zamiast [dla każdego... Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md), przykład pokazuje `For`... `Next` instrukcja, która iteruje w kolejności malejącej. W przykładzie zastosowano tę technikę `removeAt` , ponieważ metoda powoduje, że elementy po usuniętym elemencie mają niższą wartość indeksu.  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje iterację przez Wyliczenie zadeklarowane za pomocą [instrukcji enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie parametry instrukcji używają klasy, która ma `+`przeciążenia operatora dla operatorów, `-`, `>=`i `<=` .  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.List%601>
- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Kolekcje](../../programming-guide/concepts/collections.md)
