---
title: For Each...Next, instrukcja
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
ms.openlocfilehash: 0feb938121a97b06509b472652e6a753841ab2b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404657"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next — Instrukcja (Visual Basic)

Powtarza grupę instrukcji dla każdego elementu w kolekcji.

## <a name="syntax"></a>Składnia

```vb
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
|`datatype`|Opcjonalne Jeśli [`Option Infer`](option-infer-statement.md) jest włączone (wartość domyślna) lub `element` jest już zadeklarowane; wymagane, jeśli `Option Infer` jest wyłączone i `element` nie jest już zadeklarowane. Typ danych `element` .|
|`group`|Wymagany. Zmienna z typem, który jest typem kolekcji lub obiektem. Odwołuje się do kolekcji, w której mają `statements` być powtarzane.|
|`statements`|Opcjonalny. Co najmniej jedna instrukcja między `For Each` i `Next` , która jest uruchamiana dla każdego elementu w `group` .|
|`Continue For`|Opcjonalny. Przenosi kontrolę na początek `For Each` pętli.|
|`Exit For`|Opcjonalny. Przenosi kontrolę z `For Each` pętli.|
|`Next`|Wymagany. Kończy definicję `For Each` pętli.|

## <a name="simple-example"></a>Prosty przykład

Użyj `For Each` pętli... `Next` , jeśli chcesz powtórzyć zestaw instrukcji dla każdego elementu kolekcji lub tablicy.

> [!TIP]
> A [dla... Następna instrukcja](for-next-statement.md) działa prawidłowo, gdy można skojarzyć każdą iterację pętli z zmienną kontroli i określić początkową i końcową wartość tej zmiennej. Jednak podczas pracy z kolekcją pojęcie wartości początkowych i końcowych nie ma znaczenia, a użytkownik nie musi wiedzieć, ile elementów ma kolekcja. W tym rodzaju przypadku `For Each` pętla... `Next` jest często lepszym wyborem.

W poniższym przykładzie,.. `For Each` .`Next` instrukcja wykonuje iterację przez wszystkie elementy kolekcji list.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Aby uzyskać więcej przykładów, zobacz [kolekcje](../../../standard/collections/index.md) i [tablice](../../programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Pętle zagnieżdżone

Pętle można zagnieżdżać `For Each` , umieszczając jedną pętlę w innej.

W poniższym przykładzie pokazano zagnieżdżonych `For Each` ...`Next` ds.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Podczas zagnieżdżania pętli Każda pętla musi mieć unikatową `element` zmienną.

Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Zamknij i Kontynuuj dla

Instrukcja [Exit for](exit-statement.md) powoduje wyjście z `For` ...`Next` Pętla i przeniesie sterowanie do instrukcji, która następuje po `Next` instrukcji.

`Continue For`Instrukcja natychmiast przenosi kontrolę do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](continue-statement.md).

Poniższy przykład pokazuje, jak używać `Continue For` `Exit For` instrukcji i.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

W pętli można umieścić dowolną liczbę `Exit For` instrukcji `For Each` . W przypadku użycia w `For Each` pętlach zagnieżdżonych `Exit For` powoduje wyjście z wewnętrznej pętli i przeniesienie kontroli do następnego wyższego poziomu zagnieżdżenia.

`Exit For`jest często używany po ocenie pewnego stanu, na przykład w `If` ... `Then` ...`Else` XML. Może być konieczne użycie `Exit For` następujących warunków:

- Kontynuowanie iteracji jest niepotrzebne lub niemożliwe. Może to być spowodowane błędną wartością lub żądaniem zakończenia.

- Wyjątek jest przechwytywany w `Try` ... `Catch` ...`Finally`. Możesz użyć `Exit For` na końcu `Finally` bloku.

- Istnieje nieskończona pętla, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Jeśli wykryjesz taki warunek, możesz użyć, `Exit For` Aby wyjść z pętli. Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](do-loop-statement.md).

## <a name="iterators"></a>Iteratory

Za pomocą *iteratora* można wykonać niestandardową iterację w kolekcji. Iterator może być funkcją lub `Get` akcesorem. Używa instrukcji, `Yield` Aby zwrócić każdy element kolekcji pojedynczo.

Należy wywołać iterator przy użyciu `For Each...Next` instrukcji. Każda iteracja `For Each` pętli wywołuje iterator. Po `Yield` osiągnięciu instrukcji w iteratorze `Yield` zwracane jest wyrażenie w instrukcji, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu iteratora.

Poniższy przykład używa funkcji iteratora. Funkcja iteratora zawiera `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](for-next-statement.md) pętla. W `ListEvenNumbers` metodzie każda iteracja `For Each` treści instrukcji tworzy wywołanie funkcji iteratora, która przechodzi do następnej `Yield` instrukcji.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md), [instrukcja Yield](yield-statement.md)i [iterator](../modifiers/iterator.md).

## <a name="technical-implementation"></a>Realizacja techniczna

Gdy `For Each` ...`Next` zostanie uruchomiona instrukcja, Visual Basic oblicza tylko jeden raz, zanim zostanie uruchomiona pętla. Jeśli instrukcja zablokuje zmiany `element` lub zmiany `group` nie wpłyną na iterację pętli.

Gdy wszystkie elementy w kolekcji zostały po raz kolejny przypisane do `element` , `For Each` Pętla przestanie działać i kontrola przechodzi do instrukcji następującej po `Next` instrukcji.

Jeśli [opcja wnioskowanie](option-infer-statement.md) jest włączona (ustawienie domyślne), kompilator Visual Basic może wywnioskować typ danych `element` . Jeśli jest wyłączona i `element` nie została zadeklarowana poza pętlą, należy zadeklarować ją w `For Each` instrukcji. Aby jawnie zadeklarować typ danych `element` , należy użyć `As` klauzuli. Chyba że typ danych elementu jest zdefiniowany poza konstrukcja.. `For Each` . `Next` , jego zakres jest treścią pętli. Należy zauważyć, że nie można zadeklarować `element` jednocześnie zewnątrz i wewnątrz pętli.

Opcjonalnie można określić `element` w `Next` instrukcji. Poprawia to czytelność programu, zwłaszcza jeśli istnieją zagnieżdżone `For Each` pętle. Należy określić tę samą zmienną, która pojawia się w odpowiedniej `For Each` instrukcji.

Można uniknąć zmiany wartości `element` wewnątrz pętli. Może to utrudnić odczytywanie i debugowanie kodu. Zmiana wartości `group` nie ma wpływu na kolekcję lub jej elementy, które zostały określone podczas pierwszego wprowadzenia pętli.

Gdy są zagnieżdżane pętle, jeśli zostanie `Next` napotkana instrukcja zewnętrznego poziomu zagnieżdżenia przed `Next` poziomem wewnętrzny, kompilator sygnalizuje błąd. Jednak kompilator może wykryć ten błąd nakładający się tylko wtedy, gdy określisz `element` w każdej `Next` instrukcji.

Jeśli kod zależy od przechodzenia do kolekcji w określonej kolejności, `For Each` pętla... `Next` nie jest najlepszym wyborem, chyba że znane są właściwości obiektu modułu wyliczającego. Kolejność przechodzenia nie jest określana przez Visual Basic, ale przez <xref:System.Collections.IEnumerator.MoveNext%2A> metodę obiektu modułu wyliczającego. W związku z tym może nie być możliwe przewidywalnie, który element kolekcji jest pierwszy do zwrócenia w `element` , lub który jest kolejnym, który ma zostać zwrócony po danym elemencie. Możesz uzyskać bardziej niezawodne wyniki przy użyciu innej struktury pętli, takiej jak `For` ... `Next` lub `Do` . `Loop` ..

Środowisko uruchomieniowe musi mieć możliwość konwersji elementów w `group` na `element` . Instrukcja [ `Option Strict` ] kontroluje, czy dozwolone są zarówno konwersje rozszerzające, jak i wąskie ( `Option Strict` jest wyłączone, jego wartość domyślna) czy dozwolone są tylko konwersje rozszerzające ( `Option Strict` jest on włączony). Aby uzyskać więcej informacji, zobacz temat [zwężanie konwersji](#narrowing-conversions).

Typ danych `group` musi być typem referencyjnym, który odwołuje się do kolekcji lub tablicy, która jest wyliczalna. Najczęściej oznacza to, że `group` odwołuje się do obiektu, który implementuje <xref:System.Collections.IEnumerable> Interfejs `System.Collections` przestrzeni nazw lub <xref:System.Collections.Generic.IEnumerable%601> Interfejs `System.Collections.Generic` przestrzeni nazw. `System.Collections.IEnumerable`definiuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę, która zwraca obiekt modułu wyliczającego dla kolekcji. Obiekt Enumerator implementuje `System.Collections.IEnumerator` Interfejs `System.Collections` przestrzeni nazw i uwidacznia <xref:System.Collections.IEnumerator.Current%2A> Właściwość oraz <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> metody i. Visual Basic używa ich do przechodzenia do kolekcji.

### <a name="narrowing-conversions"></a>Konwersje zawężające

Gdy `Option Strict` jest ustawiona na `On` , zawężanie konwersji zwykle powoduje błędy kompilatora. Jednakże w `For Each` instrukcji konwersje z elementów w `group` do `element` są oceniane i wykonywane w czasie wykonywania, a błędy kompilatora spowodowane przez zawężanie konwersji są pomijane.

W poniższym przykładzie przypisanie `m` jako wartość początkowa dla elementu `n` nie kompiluje, gdy `Option Strict` jest włączone, ponieważ konwersja `Long` do a `Integer` jest konwersją wąskią. W `For Each` instrukcji nie jest jednak raportowany błąd kompilatora, mimo że przypisanie do `number` wymaga tej samej konwersji z `Long` do `Integer` . W instrukcji zawierającej `For Each` dużą liczbę błąd czasu wykonywania występuje, gdy <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> jest stosowany do dużej liczby.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Wywołania IEnumerator

Po `For Each` uruchomieniu pętli... `Next` pętla Visual Basic sprawdza, czy `group` odwołuje się do prawidłowego obiektu kolekcji. Jeśli nie, zgłasza wyjątek. W przeciwnym razie wywołuje <xref:System.Collections.IEnumerator.MoveNext%2A> metodę i <xref:System.Collections.IEnumerator.Current%2A> właściwość obiektu modułu wyliczającego w celu zwrócenia pierwszego elementu. Jeśli `MoveNext` wskazuje, że nie ma następnego elementu, czyli jeśli kolekcja jest pusta, `For Each` Pętla przestanie działać i kontrola przechodzi do instrukcji następującej po `Next` instrukcji. W przeciwnym razie Visual Basic ustawia jako `element` pierwszy element i uruchamia blok instrukcji.

Za każdym razem, gdy Visual Basic napotka `Next` instrukcję, wraca do `For Each` instrukcji. Ponownie wywołuje `MoveNext` i `Current` zwraca następny element, a następnie ponownie uruchamia blok lub przerywa pętlę w zależności od wyniku. Ten proces jest kontynuowany do momentu `MoveNext` , gdy nie ma żadnego elementu Next ani `Exit For` instrukcji.

**Modyfikowanie kolekcji.** Obiekt modułu wyliczającego zwrócony przez <xref:System.Collections.IEnumerable.GetEnumerator%2A> zwykle nie pozwala na zmianę kolekcji poprzez dodanie, usunięcie, zastąpienie lub zmianę kolejności elementów. W przypadku zmiany kolekcji po zainicjowaniu `For Each` pętli... `Next` obiekt modułu wyliczającego jest nieprawidłowy, a kolejna próba uzyskania dostępu do elementu powoduje <xref:System.InvalidOperationException> wyjątek.

Jednak ten blok modyfikacji nie jest określany przez Visual Basic, ale raczej przez implementację <xref:System.Collections.IEnumerable> interfejsu. Istnieje możliwość wdrożenia `IEnumerable` w sposób umożliwiający modyfikację podczas iteracji. Jeśli rozważasz taką modyfikację dynamiczną, upewnij się, że rozumiesz charakterystykę `IEnumerable` implementacji w używanej kolekcji.

**Modyfikowanie elementów kolekcji.** <xref:System.Collections.IEnumerator.Current%2A>Właściwość obiektu Enumerator jest [tylko do odczytu](../modifiers/readonly.md)i zwraca lokalną kopię każdego elementu kolekcji. Oznacza to, że nie można modyfikować samych elementów w `For Each` pętli... `Next` . Wszelkie wprowadzone zmiany mają wpływ tylko na kopię lokalną z `Current` i nie są odzwierciedlone w źródłowej kolekcji. Jeśli jednak element jest typem referencyjnym, można modyfikować członków wystąpienia, do którego wskazuje. Poniższy przykład modyfikuje `BackColor` element członkowski każdego `thisControl` elementu. Nie można jednak modyfikować `thisControl` samego siebie.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Poprzedni przykład może zmodyfikować `BackColor` składową każdego `thisControl` elementu, chociaż nie może on modyfikować `thisControl` samego siebie.

**Przechodzenie między tablicami.** Ponieważ <xref:System.Array> Klasa implementuje <xref:System.Collections.IEnumerable> interfejs, wszystkie tablice uwidaczniają <xref:System.Array.GetEnumerator%2A> metodę. Oznacza to, że można wykonać iterację tablicy z `For Each` pętlą.... `Next` Można jednak tylko odczytać elementy tablicy. Nie można ich zmienić.

## <a name="example"></a>Przykład

Poniższy przykład wyświetla listę wszystkich folderów w C:\ Katalog przy użyciu <xref:System.IO.DirectoryInfo> klasy.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje procedurę sortowania kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601> . `Car`Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> Metoda została zaimplementowana.

Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody wykonuje pojedyncze porównanie, które jest używane do sortowania. Kod pisany przez użytkownika w `CompareTo` metodzie zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większy niż zero, jeśli bieżący obiekt jest większy niż inny obiekt, i zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla wartości większej niż, mniejszej niż i równej.

W `ListCars` metodzie `cars.Sort()` instrukcja sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje `CompareTo` automatyczne wywoływanie metody dla `Car` obiektów w obiekcie `List` .

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Zobacz też

- [Kolekcje](../../../standard/collections/index.md)
- [For...Next, instrukcja](for-next-statement.md)
- [Struktury pętli](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While, instrukcja](while-end-while-statement.md)
- [Do...Loop, instrukcja](do-loop-statement.md)
- [Rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicjatory kolekcji](../../programming-guide/language-features/collection-initializers/index.md)
- [Tablice](../../programming-guide/language-features/arrays/index.md)
