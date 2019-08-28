---
title: For Each...Next — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: ebfd05a39c290e379bea2b925e7ea30c40d303fe
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046315"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next — Instrukcja (Visual Basic)

Powtarza grupę instrukcji dla każdego elementu w kolekcji.

## <a name="syntax"></a>Składnia

```
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`element`|Wymagane w `For Each` instrukcji. Opcjonalne w `Next` instrukcji. Zmiennej. Służy do iteracji elementów kolekcji.|
|`datatype`|Opcjonalne Jeśli [`Option Infer`](option-infer-statement.md) jest włączone (wartość domyślna) lub `element` jest już zadeklarowane; wymagane `Option Infer` , jeśli jest `element` wyłączone i nie jest już zadeklarowane. Typ `element`danych.|
|`group`|Wymagany. Zmienna z typem, który jest typem kolekcji lub obiektem. Odwołuje się do kolekcji, w `statements` której mają być powtarzane.|
|`statements`|Opcjonalny. Co najmniej jedna instrukcja między `For Each` i `Next` , która jest uruchamiana dla `group`każdego elementu w.|
|`Continue For`|Opcjonalny. Przenosi kontrolę na początek `For Each` pętli.|
|`Exit For`|Opcjonalny. Przenosi kontrolę z `For Each` pętli.|
|`Next`|Wymagany. Kończy definicję `For Each` pętli.|

## <a name="simple-example"></a>Prosty przykład

`For Each`Użyj... `Next` pętla, gdy chcesz powtórzyć zestaw instrukcji dla każdego elementu kolekcji lub tablicy.

> [!TIP]
> A [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) działa prawidłowo, gdy można skojarzyć każdą iterację pętli z zmienną kontroli i określić początkową i końcową wartość tej zmiennej. Jednak podczas pracy z kolekcją pojęcie wartości początkowych i końcowych nie ma znaczenia, a użytkownik nie musi wiedzieć, ile elementów ma kolekcja. W tym rodzaju przypadku `For Each`... `Next` pętla jest często lepszym wyborem.

W poniższym przykładzie, `For Each`...`Next` instrukcja wykonuje iterację przez wszystkie elementy kolekcji list.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Aby uzyskać więcej przykładów, zobacz [kolekcje](../../../standard/collections/index.md) i [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Pętle zagnieżdżone

Pętle można `For Each` zagnieżdżać, umieszczając jedną pętlę w innej.

W poniższym przykładzie pokazano zagnieżdżonych `For Each`...`Next` ds.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Podczas zagnieżdżania pętli Każda pętla musi mieć unikatową `element` zmienną.

Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Zamknij i Kontynuuj dla

Instrukcja [Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) powoduje wyjście `For`z...`Next` Pętla i przeniesie sterowanie do instrukcji, która `Next` następuje po instrukcji.

`Continue For` Instrukcja natychmiast przenosi kontrolę do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).

Poniższy przykład pokazuje, jak używać `Continue For` instrukcji i. `Exit For`

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

W pętli można umieścić dowolną liczbę `Exit For` instrukcji. `For Each` W przypadku użycia w `For Each` `Exit For` pętlach zagnieżdżonych powoduje wyjście z wewnętrznej pętli i przeniesienie kontroli do następnego wyższego poziomu zagnieżdżenia.

`Exit For`jest często używany po ocenie pewnego stanu, na przykład w `If`... `Then`... `Else` struktura. Może być konieczne użycie `Exit For` następujących warunków:

- Kontynuowanie iteracji jest niepotrzebne lub niemożliwe. Może to być spowodowane błędną wartością lub żądaniem zakończenia.

- Wyjątek jest przechwytywany w `Try`... `Catch`... `Finally`. Możesz użyć `Exit For` na końcu `Finally` bloku.

- Istnieje nieskończona pętla, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Jeśli wykryjesz taki warunek, możesz użyć `Exit For` , aby wyjść z pętli. Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>Iteratory

Za pomocą *iteratora* można wykonać niestandardową iterację w kolekcji. Iterator może być funkcją lub `Get` akcesorem. Używa `Yield` instrukcji, aby zwrócić każdy element kolekcji pojedynczo.

Należy wywołać iterator przy użyciu `For Each...Next` instrukcji. Każda iteracja `For Each` pętli wywołuje iterator. Po osiągnięciu `Yield`instrukcjiw iteratorze zwracane jest wyrażenie w instrukcji, a bieżąca lokalizacja w kodzie jest zachowywana. `Yield` Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu iteratora.

Poniższy przykład używa funkcji iteratora. Funkcja iteratora zawiera `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. W metodzie każda iteracja `For Each` treści instrukcji tworzy wywołanie funkcji iteratora, która przechodzi do następnej `Yield` instrukcji. `ListEvenNumbers`

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Aby uzyskać więcej informacji, [](../../programming-guide/concepts/iterators.md)zobacz Iteratory, [instrukcja Yield](../../../visual-basic/language-reference/statements/yield-statement.md)i [iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Realizacja techniczna

`For Each`Gdy...`Next` zostanie uruchomiona instrukcja, Visual Basic oblicza tylko jeden raz, zanim zostanie uruchomiona pętla. Jeśli instrukcja zablokuje `element` zmiany `group`lub zmiany nie wpłyną na iterację pętli.

Gdy wszystkie elementy w kolekcji zostały po raz kolejny przypisane do `element` `For Each` , pętla przestanie działać i kontrola przechodzi `Next` do instrukcji następującej po instrukcji.

Jeśli [opcja wnioskowanie](option-infer-statement.md) jest włączona (ustawienie domyślne), kompilator Visual Basic może wywnioskować typ `element`danych. Jeśli jest wyłączona i `element` nie została zadeklarowana poza pętlą, należy zadeklarować ją `For Each` w instrukcji. Aby `element` jawnie zadeklarować typ danych, `As` należy użyć klauzuli. Chyba że typ danych elementu jest zdefiniowany poza `For Each`... `Next` konstrukcja, jej zakres jest treścią pętli. Należy zauważyć, że nie `element` można zadeklarować jednocześnie zewnątrz i wewnątrz pętli.

Opcjonalnie można określić `element` `Next` w instrukcji. Poprawia to czytelność programu, zwłaszcza jeśli istnieją zagnieżdżone `For Each` pętle. Należy określić tę samą zmienną, która pojawia się w odpowiedniej `For Each` instrukcji.

Można uniknąć zmiany wartości `element` wewnątrz pętli. Może to utrudnić odczytywanie i debugowanie kodu. Zmiana wartości `group` nie ma wpływu na kolekcję lub jej elementy, które zostały określone podczas pierwszego wprowadzenia pętli.

Gdy są zagnieżdżane pętle, jeśli `Next` zostanie napotkana instrukcja zewnętrznego poziomu zagnieżdżenia `Next` przed poziomem wewnętrzny, kompilator sygnalizuje błąd. Jednak kompilator może wykryć ten błąd nakładający się tylko wtedy, gdy określisz `element` w każdej `Next` instrukcji.

Jeśli kod zależy od przechodzenia kolekcji w określonej kolejności, a `For Each`... `Next` pętla nie jest najlepszym wyborem, chyba że znasz charakterystykę obiektu modułu wyliczającego. Kolejność przechodzenia nie jest określana przez Visual Basic, ale przez <xref:System.Collections.IEnumerator.MoveNext%2A> metodę obiektu modułu wyliczającego. W związku z tym może nie być możliwe przewidywalnie, który element kolekcji jest pierwszy do zwrócenia w `element`, lub który jest kolejnym, który ma zostać zwrócony po danym elemencie. Możesz uzyskać bardziej niezawodne wyniki przy użyciu innej struktury pętli, takiej jak `For`... `Next` lub`Do`... `Loop`.

Środowisko uruchomieniowe musi mieć możliwość konwersji elementów w `group` na. `element` Instrukcja [`Option Strict`] kontroluje, czy dozwolone są zarówno konwersje rozszerzające, jak i wąskie (`Option Strict` jest wyłączone, jego wartość domyślna) czy dozwolone są tylko konwersje rozszerzające (`Option Strict` jest on włączony). Aby uzyskać więcej informacji, zobacz temat [zwężanie konwersji](#narrowing-conversions).

Typ `group` danych musi być typem referencyjnym, który odwołuje się do kolekcji lub tablicy, która jest wyliczalna. Najczęściej oznacza to, że `group` odwołuje się do obiektu, który <xref:System.Collections.IEnumerable> implementuje interfejs `System.Collections` przestrzeni nazw lub <xref:System.Collections.Generic.IEnumerable%601> Interfejs `System.Collections.Generic` przestrzeni nazw. `System.Collections.IEnumerable`<xref:System.Collections.IEnumerable.GetEnumerator%2A> definiuje metodę, która zwraca obiekt modułu wyliczającego dla kolekcji. Obiekt `System.Collections.IEnumerator` Enumerator implementuje <xref:System.Collections.IEnumerator.MoveNext%2A> Interfejs `System.Collections` przestrzeni nazw i <xref:System.Collections.IEnumerator.Reset%2A> uwidacznia <xref:System.Collections.IEnumerator.Current%2A> Właściwość oraz metody i. Visual Basic używa ich do przechodzenia do kolekcji.

### <a name="narrowing-conversions"></a>Konwersje zawężające

Gdy `Option Strict` jest ustawiona na `On`, zawężanie konwersji zwykle powoduje błędy kompilatora. Jednakże w `group` `element` instrukcji konwersje z elementów w do są oceniane i wykonywane w czasie wykonywania, a błędy kompilatora spowodowane przez zawężanie konwersji są pomijane. `For Each`

`m` W poniższym przykładzie przypisanie jako wartość początkowa dla elementu `n` nie kompiluje, gdy `Option Strict` jest `Integer` włączone, ponieważ konwersja do a `Long` jest konwersją wąskią. W instrukcji nie jest jednak raportowany błąd kompilatora, mimo że przypisanie do `number` wymaga tej samej konwersji z `Long` do `Integer`. `For Each` W instrukcji zawierającej dużą liczbę błąd czasu wykonywania występuje, gdy <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> jest stosowany do dużej liczby. `For Each`

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Wywołania IEnumerator

Podczas wykonywania `For Each`... zaczyna się pętla, Visual Basic sprawdza `group` , czy odwołuje się do prawidłowego obiektu kolekcji. `Next` Jeśli nie, zgłasza wyjątek. W przeciwnym razie wywołuje <xref:System.Collections.IEnumerator.MoveNext%2A> metodę <xref:System.Collections.IEnumerator.Current%2A> i właściwość obiektu modułu wyliczającego w celu zwrócenia pierwszego elementu. Jeśli `MoveNext` wskazuje, że nie ma następnego elementu, czyli jeśli kolekcja jest pusta `For Each` , pętla przestanie działać i kontrola przechodzi `Next` do instrukcji następującej po instrukcji. W przeciwnym razie Visual Basic `element` ustawia jako pierwszy element i uruchamia blok instrukcji.

Za każdym razem, gdy Visual Basic `Next` napotka instrukcję, wraca `For Each` do instrukcji. Ponownie wywołuje `MoveNext` i `Current` zwraca następny element, a następnie ponownie uruchamia blok lub przerywa pętlę w zależności od wyniku. Ten proces jest kontynuowany do momentu, gdy `MoveNext` nie ma żadnego elementu Next `Exit For` ani instrukcji.

**Modyfikowanie kolekcji.** Obiekt modułu wyliczającego <xref:System.Collections.IEnumerable.GetEnumerator%2A> zwrócony przez zwykle nie pozwala na zmianę kolekcji poprzez dodanie, usunięcie, zastąpienie lub zmianę kolejności elementów. W przypadku zmiany kolekcji po zainicjowaniu `For Each`... Pętla, obiekt modułu wyliczającego jest nieprawidłowy, a następna próba uzyskania dostępu do elementu <xref:System.InvalidOperationException> powoduje wyjątek. `Next`

Jednak ten blok modyfikacji nie jest określany przez Visual Basic, ale raczej przez implementację <xref:System.Collections.IEnumerable> interfejsu. Istnieje możliwość wdrożenia `IEnumerable` w sposób umożliwiający modyfikację podczas iteracji. Jeśli rozważasz taką modyfikację dynamiczną, upewnij się, że rozumiesz charakterystykę `IEnumerable` implementacji w używanej kolekcji.

**Modyfikowanie elementów kolekcji.** Właściwość obiektu Enumerator jest tylko do odczytu i zwraca lokalną kopię każdego elementu kolekcji. [](../../../visual-basic/language-reference/modifiers/readonly.md) <xref:System.Collections.IEnumerator.Current%2A> Oznacza to, że nie można modyfikować samych elementów w `For Each`... `Next` pętla. Wszelkie wprowadzone zmiany mają wpływ tylko na kopię lokalną `Current` z i nie są odzwierciedlone w źródłowej kolekcji. Jeśli jednak element jest typem referencyjnym, można modyfikować członków wystąpienia, do którego wskazuje. Poniższy przykład modyfikuje `BackColor` element członkowski każdego `thisControl` elementu. Nie można jednak modyfikować `thisControl` samego siebie.

```vb
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Poprzedni przykład może zmodyfikować `BackColor` składową każdego `thisControl` elementu, chociaż nie może on modyfikować `thisControl` samego siebie.

**Przechodzenie między tablicami.** Ponieważ klasa implementuje interfejs, wszystkie tablice uwidaczniają metodę. <xref:System.Array.GetEnumerator%2A> <xref:System.Collections.IEnumerable> <xref:System.Array> Oznacza to, że można wykonać iterację tablicy za pomocą `For Each`... `Next` pętla. Można jednak tylko odczytać elementy tablicy. Nie można ich zmienić.

## <a name="example"></a>Przykład

Poniższy przykład wyświetla listę wszystkich folderów w C:\ Katalog przy użyciu <xref:System.IO.DirectoryInfo> klasy.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje procedurę sortowania kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane <xref:System.Collections.Generic.List%601>w. Klasa implementuje interfejs, który wymaga, aby Metodazostałazaimplementowana.<xref:System.IComparable%601.CompareTo%2A> <xref:System.IComparable%601> `Car`

Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody wykonuje pojedyncze porównanie, które jest używane do sortowania. Kod pisany przez użytkownika w `CompareTo` metodzie zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większy niż zero, jeśli bieżący obiekt jest większy niż inny obiekt, i zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla wartości większej niż, mniejszej niż i równej.

W metodzie `cars.Sort()` instrukcja sortuje listę. `ListCars` <xref:System.Collections.Generic.List%601.Sort%2A> To wywołanie metody <xref:System.Collections.Generic.List%601> powoduje `Car` `List`automatyczne wywoływanie metody dla obiektów w obiekcie. `CompareTo`

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Zobacz także

- [Kolekcje](../../../standard/collections/index.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
