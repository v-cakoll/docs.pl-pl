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
ms.openlocfilehash: bcadcdfb2cb15bc6012ebe1964a4fc4379ba649d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370309"
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
  
|Część|Opis|  
|----------|-----------------|  
|`counter`|Wymagane w `For` instrukcji. Zmienna liczbowych. Zmienna sterująca pętli. Aby uzyskać więcej informacji, zobacz [Argument licznika](#BKMK_Counter) w dalszej części tego tematu.|  
|`datatype`|Opcjonalna. Typ danych `counter`. Aby uzyskać więcej informacji, zobacz [Argument licznika](#BKMK_Counter) w dalszej części tego tematu.|  
|`start`|Wymagana. Wyrażenie liczbowe. Początkowa wartość `counter`.|  
|`end`|Wymagana. Wyrażenie liczbowe. Końcowa wartość `counter`.|  
|`step`|Opcjonalna. Wyrażenie liczbowe. Wartość, o którą `counter` jest zwiększana za każdym razem, za pomocą pętli.|  
|`statements`|Opcjonalna. Jedna lub więcej instrukcji między `For` i `Next` uruchomioną określoną liczbę razy.|  
|`Continue For`|Opcjonalna. Transfer kontroli do następnej iteracji pętli.|  
|`Exit For`|Opcjonalna. Przekazuje sterowanie poza `For` pętli.|  
|`Next`|Wymagana. Kończy definicję `For` pętli.|  
  
> [!NOTE]
>  `To` Słowo kluczowe jest używane w tej instrukcji, aby określić zakres dla licznika. Możesz również użyć słowa kluczowego w [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md) w deklaracje tablicy. Aby uzyskać więcej informacji na temat deklaracje tablicy, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Proste przykłady  
 Możesz użyć `For`... `Next` struktury, gdy chcesz powtórzyć zbiór instrukcji określoną liczbę razy.  
  
 W poniższym przykładzie `index` zmienną rozpoczyna się od wartości 1 i jest zwiększany przy każdej iteracji pętli, kończące się po wartości `index` osiągnie 5.  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 W poniższym przykładzie `number` zmienną rozpoczyna się od 2 i została zmniejszona o 0,25 w każdej iteracji pętli, kończące się po wartości `number` będzie wynosić 0. `Step` Argument `-.25` zmniejsza wartość 0,25 w każdej iteracji pętli.  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  A [podczas... Kończy While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md) lub [zrobić... Instrukcja pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md) działa dobrze, jeśli nie znasz wcześniej ile razy należy uruchomić instrukcje w pętli. Jednak gdy spodziewasz się uruchomić pętli określoną liczbę razy, `For`... `Next` pętla jest lepszym rozwiązaniem. Liczba iteracji, należy określić podczas wpisywania w pętli.  
  
## <a name="nesting-loops"></a>Zagnieżdżanie pętle  
 Można zagnieżdżać `For` pętli przez umieszczenie pętli w innym. W poniższym przykładzie pokazano zagnieżdżonych `For`... `Next` struktur, które mają kroku różne wartości. Zewnętrzna Pętla tworzy ciąg dla każdej iteracji pętli. Wewnętrzny pętli zmniejsza zmienną licznika pętli dla każdej iteracji pętli.  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 Podczas zagnieżdżania pętli, każdej pętli musi mieć unikatową `counter` zmiennej.  
  
 Można także zagnieżdżać różne rodzaje struktur sterujących wewnątrz innych. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Zakończ dla i Kontynuuj dla  
 `Exit For` Instrukcji natychmiast kończy działanie `For`...`Next` pętli i transfer kontroli do kolejnej instrukcji `Next` instrukcji.  
  
 `Continue For` Instrukcji sterowania natychmiast przenosi do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [nadal instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Poniższy przykład ilustruje użycie `Continue For` i `Exit For` instrukcji.  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 Można umieścić dowolną liczbę `Exit For` instrukcji w `For`...`Next` loop. Gdy jest używana w ramach zagnieżdżonych `For`...`Next` pętle, `Exit For` opuszcza pętlę najbardziej i przekazuje sterowanie do następnego wyższy poziom zagnieżdżenia.  
  
 `Exit For` jest często używana, po przeprowadzeniu oceny jakiś warunek (na przykład w `If`... `Then`... `Else` struktury). Możesz chcieć użyć `Exit For` następujące warunki:  
  
-   Iterowanie w dalszym ciągu jest niepotrzebne lub wręcz niemożliwe. Błędna wartość lub żądania przerwania może utworzyć ten warunek.  
  
-   A `Try`... `Catch`... `Finally` instrukcji przechwytuje wyjątek. Można na przykład `Exit For` na końcu `Finally` bloku.  
  
-   Masz nieskończonej pętli, czyli pętlę, która może działać dużych lub nawet nieskończona liczba prób. Jeśli zostaną wykryte tych warunków, można użyć `Exit For` jako znak ucieczki dla pętli. Aby uzyskać więcej informacji, zobacz [zrobić... Instrukcja pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Gdy `For`... `Next` rozpoczyna pętli, Visual Basic ocenia `start`, `end`, i `step`. Visual Basic ocenia te wartości tylko w tym czasie, a następnie przypisuje `start` do `counter`. Przed instrukcją bloku jest uruchomiony, Visual Basic porównuje `counter` do `end`. Jeśli `counter` już jest większy niż `end` wartość (lub w przypadku mniejszych `step` ma wartość ujemną), `For` zakończeniu pętli i kontrola przechodzi do instrukcji następującej `Next` instrukcji. W przeciwnym razie działa blok instrukcji.  
  
 Każdym języka Visual Basic napotyka `Next` instrukcji, zwiększa `counter` przez `step` i zwraca do `For` instrukcji. Ponownie porównuje `counter` do `end`, i ponownie go uruchamia blok albo kończy pętli, w zależności od wyniku. Ten proces jest kontynuowany do momentu `counter` przekazuje `end` lub `Exit For` napotkania instrukcji.  
  
 Pętla nie zatrzymuje aż `counter` został przekazany `end`. Jeśli `counter` jest równa `end`, pętla będzie kontynuowane. To porównanie, który określa, czy należy uruchomić bloku `counter`  <=  `end` Jeśli `step` jest dodatnia i `counter`  >=  `end` Jeśli `step` jest ujemna.  
  
 Jeśli zmienisz wartość `counter` znajduje się wewnątrz pętli, może być trudniejsze do odczytywania i debugowania kodu. Zmiana wartości `start`, `end`, lub `step` nie ma wpływu na wartości iteracji, które zostały określone, jeśli pętla została najpierw wprowadzona.  
  
 Jeśli możesz zagnieździć pętli, kompilator sygnalizuje błąd, jeśli napotka `Next` instrukcji zewnętrzne poziom zagnieżdżenia, przed `Next` instrukcji wewnętrzny poziom. Jednak kompilator to wykryć nakładających się błąd, tylko wtedy, gdy należy określić `counter` w każdym `Next` instrukcji.  
  
### <a name="step-argument"></a>Argument kroku  
 Wartość `step` może być dodatnia lub ujemna. Ten parametr określa przetwarzanie pętli zgodnie z poniższą tabelą:  
  
|**Wartość kroku**|**Pętla jest wykonywana Jeśli**|  
|--------------------|--------------------------|  
|Dodatnia lub równa zero|`counter` <= `end`|  
|Ujemne|`counter` >= `end`|  
  
 Wartość domyślna `step` 1.  
  
### <a name="BKMK_Counter"></a> Argument licznika  
 Poniższa tabela wskazuje, czy `counter` definiuje Nowa zmienna lokalna, które są ograniczone do całej `For…Next` pętli. Oznaczanie zależy od tego, czy `datatype` jest obecny oraz tego, czy `counter` jest już zdefiniowany.  
  
|Jest `datatype` obecne?|Jest `counter` już zdefiniowane?|Wynik (czy `counter` definiuje Nowa zmienna lokalna, które są ograniczone do całej `For...Next` pętli)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Nie|Tak|Nie, ponieważ `counter` jest już zdefiniowany. Jeśli zakres `counter` nie jest lokalnym do procedury występuje ostrzeżenie kompilacji.|  
|Nie|Nie|Tak. Typ danych jest wnioskowany z `start`, `end`, i `step` wyrażenia. Aby uzyskać informacji na temat wnioskowanie o typie, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Tak|Tak|Tak, ale tylko wtedy, gdy istniejące `counter` zmienna jest zdefiniowana poza procedury. Tej zmiennej pozostaje oddzielnym. Jeśli zakres istniejącego `counter` zmienna jest lokalny dla procedury, wystąpi błąd kompilacji.|  
|Tak|Nie|Tak.|  
  
 Typ danych `counter` Określa typ iteracji, która musi być jednym z następujących typów:  
  
-   A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, lub `Double`.  
  
-   Wyliczenie, które można zadeklarować przy użyciu [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   `Object`.  
  
-   Typ `T` ma następujące operatory, gdzie `B` to typ, który może być używana w `Boolean` wyrażenia.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Opcjonalnie możesz określić `counter` zmienną `Next` instrukcji. Ta składnia zwiększa czytelność program, zwłaszcza, jeśli można zagnieżdżać `For` pętli. Należy określić zmienną, która pojawia się w odpowiednich `For` instrukcji.  
  
 `start`, `end`, I `step` wyrażenia może być dowolnego typu danych, która rozszerza się na typ `counter`. Jeśli używasz typu zdefiniowanego przez użytkownika, aby uzyskać `counter`, może być konieczne zdefiniowanie `CType` operatora konwersji do konwersji typów `start`, `end`, lub `step` do typu `counter`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa wszystkie elementy z listy ogólnej. Zamiast [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md), w przykładzie pokazano `For`... `Next` instrukcja, która dokonuje iteracji w kolejności malejącej. W przykładzie użyto tej techniki, ponieważ `removeAt` metoda powoduje, że elementy po usuniętym elemencie muszą mieć niższą wartość indeksu.  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje iterację przez wyliczenie, które są zadeklarowane za pomocą [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie parametrów instrukcji użycie klasy, która ma przeciążenia `+`, `-`, `>=`, i `<=` operatorów.  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Collections.Generic.List%601>
- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Kolekcje](../../programming-guide/concepts/collections.md)
