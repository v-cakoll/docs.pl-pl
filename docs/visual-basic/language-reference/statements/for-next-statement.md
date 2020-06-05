---
title: For...Next, instrukcja
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
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404644"
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

|Część|Opis|
|----------|-----------------|
|`counter`|Wymagane w `For` instrukcji. Zmienna numeryczna. Zmienna sterująca pętli. Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.|
|`datatype`|Opcjonalny. Typ danych `counter` . Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.|
|`start`|Wymagany. Wyrażenie liczbowe. Wartość początkowa `counter` .|
|`end`|Wymagany. Wyrażenie liczbowe. Końcowa wartość parametru `counter` .|
|`step`|Opcjonalny. Wyrażenie liczbowe. Wartość, według której `counter` jest zwiększana za każdym razem przez pętlę.|
|`statements`|Opcjonalny. Co najmniej jedna instrukcja między `For` i `Next` , która uruchamia określoną liczbę razy.|
|`Continue For`|Opcjonalny. Przenosi formant do następnej iteracji pętli.|
|`Exit For`|Opcjonalny. Przenosi kontrolę z `For` pętli.|
|`Next`|Wymagany. Kończy definicję `For` pętli.|

> [!NOTE]
> `To`Słowo kluczowe jest używane w tej instrukcji, aby określić zakres dla licznika. Można również użyć słowa kluczowego [SELECT... Instrukcja Case](select-case-statement.md) i w deklaracjach tablicowych. Aby uzyskać więcej informacji na temat deklaracji tablicowych, zobacz [Dim Statement](dim-statement.md).

## <a name="simple-examples"></a>Proste przykłady

`For` `Next` Jeśli chcesz powtórzyć zestaw instrukcji przez określoną liczbę razy, użyj struktury...

W poniższym przykładzie `index` zmienna rozpoczyna się od wartości 1 i zwiększa się wraz z każdą iteracją pętli, kończąc po wartości `index` osiągnie 5.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

W poniższym przykładzie `number` zmienna zaczyna się od 2 i jest zmniejszana o 0,25 dla każdej iteracji pętli, kończąc po wartości `number` osiągnie 0. `Step`Argument `-.25` zmniejsza wartość o 0,25 dla każdej iteracji pętli.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> A [while... Instrukcja End while](while-end-while-statement.md) lub [... Instrukcja Loop](do-loop-statement.md) działa prawidłowo, gdy nie wiadomo, ile razy należy uruchomić instrukcje w pętli. Jeśli jednak oczekuje się, że pętla zostanie uruchomiona określoną liczbę razy, jest to `For` `Next` lepszy wybór pętli.... Należy określić liczbę iteracji podczas pierwszego wprowadzania pętli.

## <a name="nesting-loops"></a>Pętle zagnieżdżania

Pętle można zagnieżdżać `For` , umieszczając jedną pętlę w innej. Poniższy przykład ilustruje zagnieżdżone `For` ... `Next` struktury, które mają różne wartości kroków. Pętla zewnętrzna tworzy ciąg dla każdej iteracji pętli. Pętla wewnętrzna zmniejsza zmienną licznika pętli dla każdej iteracji pętli.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Podczas zagnieżdżania pętli Każda pętla musi mieć unikatową `counter` zmienną.

Można również zagnieżdżać różne struktury kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Zamknij i Kontynuuj dla

`Exit For`Instrukcja natychmiast opuszcza `For` ...`Next` Pętla i przeniesie sterowanie do instrukcji, która następuje po `Next` instrukcji.

`Continue For`Instrukcja natychmiast przenosi kontrolę do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](continue-statement.md).

Poniższy przykład ilustruje użycie `Continue For` `Exit For` instrukcji i.

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

Można umieścić dowolną liczbę `Exit For` instrukcji w `For` ...`Next` for. Używany w zagnieżdżonych `For` ...`Next` pętle, `Exit For` opuszcza wewnętrzna pętla i przenosi formant na następny wyższy poziom zagnieżdżenia.

`Exit For`jest często używany po dokonaniu oszacowania pewnego warunku (na przykład w `If` ... `Then` ...`Else` Struktura). Może być konieczne użycie `Exit For` następujących warunków:

- Kontynuowanie iteracji jest niepotrzebne lub niemożliwe. Wartość błędna lub żądanie zakończenia może stworzyć ten warunek.

- A `Try` ... `Catch` ...`Finally` Instrukcja przechwytuje wyjątek. Możesz użyć `Exit For` na końcu `Finally` bloku.

- Masz nieskończoną pętlę, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Jeśli wykryjesz taki warunek, możesz użyć, `Exit For` Aby wyjść z pętli. Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](do-loop-statement.md).

## <a name="technical-implementation"></a>Realizacja techniczna

Gdy `For` `Next` zostanie rozpoczęta pętla..., Visual Basic oblicza `start` , `end` , i `step` . Visual Basic oblicza te wartości tylko w tym momencie, a następnie przypisuje `start` do `counter` . Przed uruchomieniem bloku instrukcji Visual Basic porównuje `counter` z `end` . Jeśli `counter` jest już większa niż `end` wartość (lub mniejsza, jeśli `step` jest ujemna), `For` Pętla kończy się i kontrola przechodzi do instrukcji, która następuje po `Next` instrukcji. W przeciwnym razie blok instrukcji zostanie uruchomiony.

Za każdym razem, gdy Visual Basic napotkają `Next` instrukcję, zwiększa się `counter` przez `step` i wraca do `For` instrukcji. Ponownie porównuje `counter` z `end` , a następnie uruchamia blok lub zamyka pętlę, w zależności od wyniku. Ten proces jest kontynuowany do momentu przełączenia `counter` `end` lub wykonania `Exit For` instrukcji.

Pętla nie jest zatrzymywana do momentu przełączenia `counter` `end` . Jeśli `counter` jest równe `end` , pętla kontynuuje działanie. Porównanie, które określa, czy ma być uruchamiany blok, ma wartość `counter`  <=  `end` `step` dodatnią, a `counter`  >=  `end` Jeśli `step` jest ujemna.

Jeśli zmienisz wartość `counter` while wewnątrz pętli, kod może być trudniejszy do odczytania i debugowania. Zmiana wartości `start` , `end` lub `step` nie wpływa na wartości iteracji, które zostały określone podczas pierwszego wprowadzenia pętli.

Jeśli zagnieżdżasz pętle, kompilator sygnalizuje błąd, jeśli napotka instrukcję na `Next` zewnętrznym poziomie zagnieżdżenia przed `Next` instrukcją wewnętrznego poziomu. Jednak kompilator może wykryć ten błąd nakładający się tylko wtedy, gdy określisz `counter` w każdej `Next` instrukcji.

### <a name="step-argument"></a>Argument kroku

Wartość `step` może być dodatnia lub ujemna. Ten parametr określa przetwarzanie pętli zgodnie z poniższą tabelą:

|**Wartość kroku**|**Pętla jest wykonywana, jeśli**|
|--------------------|--------------------------|
|Wartość dodatnia lub zero|`counter` <= `end`|
|Ujemne|`counter` >= `end`|

Wartość domyślna elementu `step` to 1.

### <a name="counter-argument"></a><a name="BKMK_Counter"></a>Argument licznika

Poniższa tabela wskazuje, czy `counter` definiuje nową zmienną lokalną, która jest objęta zakresem całej `For…Next` pętli. To określenie zależy od tego `datatype` , czy jest obecne i czy `counter` jest już zdefiniowane.

|Czy `datatype` istnieje?|Czy jest `counter` już zdefiniowany?|Wynik (czy `counter` definiuje nową zmienną lokalną, która jest objęta zakresem całej `For...Next` pętli)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Nie|Yes|Nie, ponieważ `counter` jest już zdefiniowany. Jeśli zakres `counter` nie jest lokalny dla procedury, występuje ostrzeżenie w czasie kompilacji.|
|Nie|Nie|Tak. Typ danych jest wywnioskowany na podstawie `start` wyrażeń, `end` i `step` . Aby uzyskać informacje na temat wnioskowania o typie, zobacz [instrukcja SELECT](option-infer-statement.md) i [wnioskowanie typu lokalnego](../../programming-guide/language-features/variables/local-type-inference.md).|
|Tak|Tak|Tak, ale tylko wtedy, gdy istniejąca `counter` zmienna jest zdefiniowana poza procedurą. Ta zmienna pozostaje oddzielona. Jeśli zakres istniejącej `counter` zmiennej jest lokalny dla procedury, wystąpi błąd w czasie kompilacji.|
|Yes|Nie|Tak.|

Typ danych `counter` określa typ iteracji, który musi być jednym z następujących typów:

- A `Byte` ,,,,,,,,, `SByte` `UShort` `Short` `UInteger` `Integer` `ULong` `Long` `Decimal` `Single` lub `Double` .

- Wyliczenie zadeklarowane za pomocą [instrukcji enum](enum-statement.md).

- A `Object` .

- Typ `T` , który ma następujące operatory, gdzie `B` jest typem, który może być używany w `Boolean` wyrażeniu.

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

Opcjonalnie możesz określić `counter` zmienną w `Next` instrukcji. Ta składnia zwiększa czytelność programu, zwłaszcza jeśli istnieją zagnieżdżone `For` pętle. Należy określić zmienną, która pojawia się w odpowiedniej `For` instrukcji.

`start`Wyrażenia, `end` i `step` mogą być oceniane do dowolnego typu danych, który jest rozszerzany do typu `counter` . Jeśli używasz typu zdefiniowanego przez użytkownika dla `counter` , może być konieczne zdefiniowanie `CType` operatora konwersji, aby przekonwertować typy `start` , `end` lub `step` na typ `counter` .

## <a name="example"></a>Przykład

Poniższy przykład usuwa wszystkie elementy z listy ogólnej. Zamiast [dla każdego... Next](for-each-next-statement.md)— przykład pokazuje `For` instrukcję..., `Next` która iteruje w kolejności malejącej. W przykładzie zastosowano tę technikę, ponieważ `removeAt` Metoda powoduje, że elementy po usuniętym elemencie mają niższą wartość indeksu.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Przykład

Poniższy przykład wykonuje iterację przez Wyliczenie zadeklarowane za pomocą [instrukcji enum](enum-statement.md).

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Przykład

W poniższym przykładzie parametry instrukcji używają klasy, która ma przeciążenia operatora dla `+` `-` operatorów,, `>=` i `<=` .

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic.List%601>
- [Struktury pętli](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While, instrukcja](while-end-while-statement.md)
- [Do...Loop, instrukcja](do-loop-statement.md)
- [Zagnieżdżone struktury sterujące](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit, instrukcja](exit-statement.md)
- [Kolekcje](../../programming-guide/concepts/collections.md)
