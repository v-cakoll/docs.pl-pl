---
title: For...Next — Instrukcja
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
ms.openlocfilehash: 3cae44abb8e790542f11e6c5a5f1e317675ff988
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351187"
---
# <a name="fornext-statement-visual-basic"></a>For...Next — Instrukcja (Visual Basic)

Powtarza grupę instrukcji określoną liczbę razy.

## <a name="syntax"></a>Składnia

```vb
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
|`counter`|Wymagane w instrukcji `For`. Zmienna numeryczna. Zmienna sterująca pętli. Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.|
|`datatype`|Opcjonalna. Typ danych `counter`. Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.|
|`start`|Wymagana. Wyrażenie liczbowe. Początkowa wartość `counter`.|
|`end`|Wymagana. Wyrażenie liczbowe. Końcowa wartość `counter`.|
|`step`|Opcjonalna. Wyrażenie liczbowe. Wielkość, o jaką `counter` jest zwiększana za każdym razem przez pętlę.|
|`statements`|Opcjonalna. Jedna lub więcej instrukcji między `For` i `Next`, które uruchamiają określoną liczbę razy.|
|`Continue For`|Opcjonalna. Przenosi formant do następnej iteracji pętli.|
|`Exit For`|Opcjonalna. Przenosi kontrolę z pętli `For`.|
|`Next`|Wymagana. Kończy definicję pętli `For`.|

> [!NOTE]
> W tej instrukcji użyto słowa kluczowego `To`, aby określić zakres dla licznika. Można również użyć słowa kluczowego [SELECT... Instrukcja Case](../../../visual-basic/language-reference/statements/select-case-statement.md) i w deklaracjach tablicowych. Aby uzyskać więcej informacji na temat deklaracji tablicowych, zobacz [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).

## <a name="simple-examples"></a>Proste przykłady

Możesz użyć struktury `For`...`Next`, gdy chcesz powtórzyć zestaw instrukcji określoną liczbę razy.

W poniższym przykładzie zmienna `index` rozpoczyna się od wartości 1 i zwiększa się wraz z każdą iteracją pętli, kończąc po wartości `index` osiągnie 5.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

W poniższym przykładzie zmienna `number` zaczyna się od 2 i jest zmniejszana o 0,25 dla każdej iteracji pętli, kończąc po wartości `number` osiągnie 0. `Step` argument `-.25` zmniejsza wartość o 0,25 dla każdej iteracji pętli.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> A [while... Instrukcja End while](../../../visual-basic/language-reference/statements/while-end-while-statement.md) lub [... Instrukcja Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) działa prawidłowo, gdy nie wiadomo, ile razy należy uruchomić instrukcje w pętli. Jeśli jednak oczekujesz, że pętla zostanie uruchomiona określoną liczbę razy, jest to lepszy wybór `For`...`Next` pętla. Należy określić liczbę iteracji podczas pierwszego wprowadzania pętli.

## <a name="nesting-loops"></a>Pętle zagnieżdżania

Pętle `For` można zagnieżdżać, umieszczając jedną pętlę w innej. Poniższy przykład ilustruje zagnieżdżone `For`...`Next` struktury, które mają różne wartości kroków. Pętla zewnętrzna tworzy ciąg dla każdej iteracji pętli. Pętla wewnętrzna zmniejsza zmienną licznika pętli dla każdej iteracji pętli.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Podczas zagnieżdżania pętli Każda pętla musi mieć unikatową zmienną `counter`.

Można również zagnieżdżać różne struktury kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Zamknij i Kontynuuj dla

Instrukcja `Exit For` natychmiast opuszcza `For`...`Next` Pętla i przeniesie sterowanie do instrukcji, która następuje po instrukcji `Next`.

Instrukcja `Continue For` powoduje natychmiastowe przeniesienie kontroli do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).

Poniższy przykład ilustruje użycie instrukcji `Continue For` i `Exit For`.

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

W `For`można umieścić dowolną liczbę instrukcji `Exit For`...`Next` For. Używane w zagnieżdżonych `For`...`Next` pętle, `Exit For` opuszcza wewnętrzna pętla i przeniesie kontrolę na następny wyższy poziom zagnieżdżenia.

`Exit For` jest często używana po dokonaniu oszacowania pewnego warunku (na przykład w `If`...`Then`... struktury`Else`). Możesz chcieć użyć `Exit For` z następujących warunków:

- Kontynuowanie iteracji jest niepotrzebne lub niemożliwe. Wartość błędna lub żądanie zakończenia może stworzyć ten warunek.

- Instrukcja `Try`...`Catch`...`Finally` przechwytuje wyjątek. Na końcu bloku `Finally` możesz użyć `Exit For`.

- Masz nieskończoną pętlę, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Jeśli wykryjesz taki warunek, możesz użyć `Exit For`, aby wyjść z pętli. Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="technical-implementation"></a>Realizacja techniczna

Gdy rozpocznie się pętla `For`...`Next`, Visual Basic oblicza `start`, `end`i `step`. Visual Basic oblicza te wartości tylko w tym momencie, a następnie przypisuje `start` do `counter`. Przed uruchomieniem bloku instrukcji Visual Basic porównuje `counter` z `end`. Jeśli `counter` jest już większa niż `end` wartość (lub mniejsza, jeśli `step` jest ujemna), pętla `For` kończy się i kontrola przechodzi do instrukcji, która następuje po instrukcji `Next`. W przeciwnym razie blok instrukcji zostanie uruchomiony.

Za każdym razem, gdy Visual Basic napotka instrukcję `Next`, zwiększa `counter` przez `step` i powraca do instrukcji `For`. Ponownie porównuje `counter` z `end`i ponownie uruchamia blok lub opuszcza pętlę, w zależności od wyniku. Ten proces jest kontynuowany do momentu `counter` przekazywać `end` lub napotkania instrukcji `Exit For`.

Pętla nie jest zatrzymywana, dopóki `counter` nie przeszedł `end`. Jeśli `counter` jest równa `end`, pętla będzie kontynuowana. Porównanie, które określa, czy uruchomić blok jest `counter` <= `end` Jeśli `step` jest dodatni i `counter` >= `end`, jeśli `step` jest ujemna.

Jeśli zmienisz wartość `counter` w obrębie pętli, kod może być trudniejszy do odczytania i debugowania. Zmiana wartości `start`, `end`lub `step` nie ma wpływu na wartości iteracji, które zostały określone podczas pierwszego wprowadzenia pętli.

Jeśli zagnieżdżasz pętle, kompilator sygnalizuje błąd, jeśli napotka `Next` instrukcji na zewnętrznym poziomie zagnieżdżenia przed instrukcją `Next` na poziomie wewnętrznym. Jednak kompilator może wykryć ten błąd nakładający się tylko wtedy, gdy określisz `counter` w każdej `Next` instrukcji.

### <a name="step-argument"></a>Argument kroku

Wartość `step` może być dodatnia lub ujemna. Ten parametr określa przetwarzanie pętli zgodnie z poniższą tabelą:

|**Wartość kroku**|**Pętla jest wykonywana, jeśli**|
|--------------------|--------------------------|
|Wartość dodatnia lub zero|`counter` <= `end`|
|Ujemne|`counter` >= `end`|

Wartość domyślna `step` to 1.

### <a name="BKMK_Counter"></a>Argument licznika

Poniższa tabela wskazuje, czy `counter` definiuje nową zmienną lokalną, która jest objęta zakresem całej pętli `For…Next`. To określenie zależy od tego, czy `datatype` jest obecny i czy `counter` jest już zdefiniowany.

|Czy `datatype` jest obecny?|Czy `counter` jest już zdefiniowany?|Wynik (czy `counter` definiuje nową zmienną lokalną, która jest objęta zakresem całej pętli `For...Next`)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Nie|Tak|Nie, ponieważ `counter` jest już zdefiniowany. Jeśli zakres `counter` nie jest lokalny dla procedury, wystąpi ostrzeżenie w czasie kompilacji.|
|Nie|Nie|Tak. Typ danych jest wywnioskowany na podstawie wyrażeń `start`, `end`i `step`. Aby uzyskać informacje na temat wnioskowania o typie, zobacz [instrukcja SELECT](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie typu lokalnego](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|
|Tak|Tak|Tak, ale tylko wtedy, gdy istniejąca zmienna `counter` jest zdefiniowana poza procedurą. Ta zmienna pozostaje oddzielona. Jeśli zakres istniejącej zmiennej `counter` jest lokalny dla procedury, wystąpi błąd w czasie kompilacji.|
|Tak|Nie|Tak.|

Typ danych `counter` określa typ iteracji, który musi być jednym z następujących typów:

- `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`lub `Double`.

- Wyliczenie zadeklarowane za pomocą [instrukcji enum](../../../visual-basic/language-reference/statements/enum-statement.md).

- `Object`.

- Typ `T`, który zawiera następujące operatory, gdzie `B` jest typem, który może być używany w wyrażeniu `Boolean`.

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

Opcjonalnie możesz określić zmienną `counter` w instrukcji `Next`. Ta składnia zwiększa czytelność programu, zwłaszcza jeśli istnieją zagnieżdżone pętle `For`. Należy określić zmienną, która pojawia się w odpowiedniej instrukcji `For`.

Wyrażenia `start`, `end`i `step` mogą być oceniane do dowolnego typu danych, który jest rozszerzany do typu `counter`. Jeśli używasz typu zdefiniowanego przez użytkownika do `counter`, może być konieczne zdefiniowanie operatora konwersji `CType`, aby skonwertować typy `start`, `end`lub `step` do typu `counter`.

## <a name="example"></a>Przykład

Poniższy przykład usuwa wszystkie elementy z listy ogólnej. Zamiast [dla każdego... Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md), przykład pokazuje instrukcję `For`...`Next`, która iteruje w kolejności malejącej. W przykładzie zastosowano tę technikę, ponieważ metoda `removeAt` powoduje, że elementy po usuniętym elemencie mają niższą wartość indeksu.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Przykład

Poniższy przykład wykonuje iterację przez Wyliczenie zadeklarowane za pomocą [instrukcji enum](../../../visual-basic/language-reference/statements/enum-statement.md).

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Przykład

W poniższym przykładzie parametry instrukcji używają klasy, która ma przeciążenia operatora dla operatorów `+`, `-`, `>=`i `<=`.

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.List%601>
- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Kolekcje](../../programming-guide/concepts/collections.md)
