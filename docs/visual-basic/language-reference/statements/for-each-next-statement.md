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
ms.openlocfilehash: f56e5defa2328011d222bfca05334b610e805055
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332786"
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
|`element`|Wymagane w instrukcji `For Each`. Opcjonalne w instrukcji `Next`. Zmiennej. Służy do iteracji elementów kolekcji.|
|`datatype`|Opcjonalne, jeśli [`Option Infer`](option-infer-statement.md) jest włączona (wartość domyślna) lub `element` jest już zadeklarowana; wymagany, jeśli `Option Infer` jest wyłączony i `element` nie jest już zadeklarowany. Typ danych `element`.|
|`group`|Wymagany. Zmienna z typem, który jest typem kolekcji lub obiektem. Odwołuje się do kolekcji, w której `statements` należy powtarzać.|
|`statements`|Opcjonalny. Jedna lub więcej instrukcji między `For Each` i `Next`, które są uruchamiane dla każdego elementu w `group`.|
|`Continue For`|Opcjonalny. Przenosi kontrolę na początek pętli `For Each`.|
|`Exit For`|Opcjonalny. Przenosi kontrolę z pętli `For Each`.|
|`Next`|Wymagany. Kończy definicję pętli `For Each`.|

## <a name="simple-example"></a>Prosty przykład

Użyj `For Each`... `Next` pętla, gdy chcesz powtórzyć zestaw instrukcji dla każdego elementu kolekcji lub tablicy.

> [!TIP]
> A [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) działa prawidłowo, gdy można skojarzyć każdą iterację pętli z zmienną kontroli i określić początkową i końcową wartość tej zmiennej. Jednak podczas pracy z kolekcją pojęcie wartości początkowych i końcowych nie ma znaczenia, a użytkownik nie musi wiedzieć, ile elementów ma kolekcja. W tym rodzaju przypadku pętla `For Each`... `Next` jest często lepszym wyborem.

W poniższym przykładzie `For Each`... `Next` instrukcja wykonuje iterację przez wszystkie elementy kolekcji list.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Aby uzyskać więcej przykładów, zobacz [kolekcje](../../../standard/collections/index.md) i [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Pętle zagnieżdżone

Można zagnieżdżać pętle `For Each` przez umieszczenie jednej pętli w innej.

Poniższy przykład ilustruje zagnieżdżony `For Each`... `Next` ds.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Podczas zagnieżdżania pętli Każda pętla musi mieć unikatową zmienną `element`.

Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Zamknij i Kontynuuj dla

Instrukcja [Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) powoduje wyjście z `For`... `Next` Pętla i transferuje sterowanie do instrukcji, która następuje po instrukcji `Next`.

Instrukcja `Continue For` przenosi bezpośrednio kontrolę do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).

Poniższy przykład pokazuje, jak używać instrukcji `Continue For` i `Exit For`.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

W pętli `For Each` można umieścić dowolną liczbę instrukcji `Exit For`. Gdy jest używany w zagnieżdżonych pętlach `For Each`, `Exit For` powoduje, że wykonanie zamyka najbliższą pętlę i przenosi kontrolę na następny wyższy poziom zagnieżdżenia.

`Exit For` jest często używany po ocenie pewnego stanu, na przykład w `If`... `Then`... `Else`. Możesz chcieć użyć `Exit For` z następujących warunków:

- Kontynuowanie iteracji jest niepotrzebne lub niemożliwe. Może to być spowodowane błędną wartością lub żądaniem zakończenia.

- Wyjątek jest przechwytywany w `Try`... `Catch`... `Finally`. Możesz użyć `Exit For` na końcu bloku `Finally`.

- Istnieje nieskończona pętla, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy. Jeśli wykryjesz taki warunek, możesz użyć `Exit For`, aby wyjść z pętli. Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>Iteratory

Za pomocą *iteratora* można wykonać niestandardową iterację w kolekcji. Iterator może być funkcją lub `Get` akcesor. Używa instrukcji `Yield`, aby zwrócić każdy element kolekcji pojedynczo.

Iterator jest wywoływany przy użyciu instrukcji `For Each...Next`. Każda iteracja pętli `For Each` wywołuje iterator. Po osiągnięciu instrukcji `Yield` w iteratoru wyrażenie w instrukcji `Yield` jest zwracane, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu iteratora.

Poniższy przykład używa funkcji iteratora. Funkcja iteratora zawiera instrukcję `Yield`, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. W metodzie `ListEvenNumbers` każda iteracja treści instrukcji `For Each` tworzy wywołanie funkcji iteratora, która przechodzi do następnej instrukcji `Yield`.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md), [instrukcja Yield](../../../visual-basic/language-reference/statements/yield-statement.md)i [iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Realizacja techniczna

Gdy `For Each`... `Next` zostanie uruchomiona instrukcja, Visual Basic oblicza tylko jeden raz, zanim zostanie uruchomiona pętla. Jeśli instrukcja blokuje zmiany `element` lub `group`, te zmiany nie wpłyną na iterację pętli.

Gdy wszystkie elementy w kolekcji zostały po razeniu przypisane do `element`, pętla `For Each` przestanie działać i kontrola przechodzi do instrukcji następującej po instrukcji `Next`.

Jeśli [opcja wnioskowanie](option-infer-statement.md) jest włączona (ustawienie domyślne), kompilator Visual Basic może wywnioskować typ danych `element`. Jeśli jest wyłączona, a `element` nie została zadeklarowana poza pętlą, należy zadeklarować ją w instrukcji `For Each`. Aby jawnie zadeklarować typ danych `element`, użyj klauzuli `As`. Jeśli typ danych elementu nie jest zdefiniowany poza konstrukcją `For Each`... `Next`, jego zakres jest treścią pętli. Należy zauważyć, że nie można zadeklarować wartości `element` zarówno na zewnątrz, jak i wewnątrz pętli.

Opcjonalnie można określić `element` w instrukcji `Next`. Poprawia to czytelność programu, zwłaszcza jeśli istnieją zagnieżdżone pętle `For Each`. Należy określić tę samą zmienną, która pojawia się w odpowiedniej instrukcji `For Each`.

Można uniknąć zmiany wartości `element` wewnątrz pętli. Może to utrudnić odczytywanie i debugowanie kodu. Zmiana wartości `group` nie ma wpływu na kolekcję lub jej elementy, które zostały określone podczas pierwszego wprowadzenia pętli.

Gdy są zagnieżdżane pętle, jeśli zostanie wykryty `Next` instrukcji zewnętrznego poziomu zagnieżdżenia przed `Next` wewnętrznego poziomu, kompilator sygnalizuje błąd. Jednak kompilator może wykryć ten błąd nakładający się tylko wtedy, gdy określisz `element` w każdej instrukcji `Next`.

Jeśli Twój kod zależy od przechodzenia do kolekcji w określonej kolejności, pętla `For Each`... `Next` nie jest najlepszym wyborem, chyba że znasz charakterystykę obiektu modułu wyliczającego. Kolejność przechodzenia nie jest określana przez Visual Basic, ale przez metodę <xref:System.Collections.IEnumerator.MoveNext%2A> obiektu modułu wyliczającego. W związku z tym może nie być możliwe przewidywalnie, który element kolekcji jest pierwszy do zwrócenia w `element` lub który jest kolejnym, który ma zostać zwrócony po danym elemencie. Możliwe jest uzyskanie bardziej niezawodnych wyników przy użyciu innej struktury pętli, takiej jak `For`... `Next` lub `Do`... `Loop`.

Środowisko uruchomieniowe musi mieć możliwość przekonwertowania elementów w `group` do `element`. Instrukcja [`Option Strict`] kontroluje, czy dozwolone są zarówno konwersje rozszerzające, jak i wąskie (`Option Strict`, jego wartość domyślna), czy tylko konwersje rozszerzające są dozwolone (`Option Strict` jest włączone). Aby uzyskać więcej informacji, zobacz temat [zwężanie konwersji](#narrowing-conversions).

Typ danych `group` musi być typem referencyjnym, który odwołuje się do kolekcji lub tablicy, która jest wyliczalna. Najczęściej oznacza to, że `group` odwołuje się do obiektu, który implementuje interfejs <xref:System.Collections.IEnumerable> dla przestrzeni nazw `System.Collections` lub <xref:System.Collections.Generic.IEnumerable%601> interfejsu przestrzeni nazw `System.Collections.Generic`. `System.Collections.IEnumerable` definiuje metodę <xref:System.Collections.IEnumerable.GetEnumerator%2A>, która zwraca obiekt modułu wyliczającego dla kolekcji. Obiekt Enumerator implementuje interfejs `System.Collections.IEnumerator` przestrzeni nazw `System.Collections` i uwidacznia Właściwość <xref:System.Collections.IEnumerator.Current%2A> oraz <xref:System.Collections.IEnumerator.Reset%2A> i <xref:System.Collections.IEnumerator.MoveNext%2A> metod. Visual Basic używa ich do przechodzenia do kolekcji.

### <a name="narrowing-conversions"></a>Konwersje zawężające

Gdy `Option Strict` jest ustawiona na `On`, zawężanie konwersji zwykle powoduje błędy kompilatora. Jednakże w instrukcji `For Each` konwersje z elementów w `group` do `element` są oceniane i wykonywane w czasie wykonywania, a błędy kompilatora spowodowane przez zawężanie konwersji są pomijane.

W poniższym przykładzie przypisanie `m` jako wartości początkowej dla `n` nie kompiluje się, gdy `Option Strict` jest włączone, ponieważ konwersja `Long` na `Integer` jest konwersją na wąskie. W instrukcji `For Each` nie raportowany jest błąd kompilatora, nawet jeśli przypisanie do `number` wymaga tej samej konwersji z `Long` do `Integer`. W instrukcji `For Each`, która zawiera dużą liczbę, wystąpi błąd czasu wykonywania, gdy <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> zostanie zastosowany do dużej liczby.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Wywołania IEnumerator

Podczas wykonywania `For Each`... `Next` pętla, Visual Basic sprawdza, czy `group` odwołuje się do prawidłowego obiektu kolekcji. Jeśli nie, zgłasza wyjątek. W przeciwnym razie wywołuje metodę <xref:System.Collections.IEnumerator.MoveNext%2A> i Właściwość <xref:System.Collections.IEnumerator.Current%2A> obiektu modułu wyliczającego w celu zwrócenia pierwszego elementu. Jeśli `MoveNext` wskazuje, że nie ma następnego elementu, czyli jeśli kolekcja jest pusta, pętla `For Each` przestanie działać i kontrola przechodzi do instrukcji następującej po instrukcji `Next`. W przeciwnym razie Visual Basic ustawia `element` do pierwszego elementu i uruchamia blok instrukcji.

Za każdym razem, gdy Visual Basic napotka instrukcję `Next`, wraca do instrukcji `For Each`. Ponownie wywołuje `MoveNext` i `Current` do zwrócenia następnego elementu, a następnie ponownie uruchamia blok lub przerywa pętlę w zależności od wyniku. Ten proces jest kontynuowany do momentu, gdy `MoveNext` wskazuje, że nie ma żadnego elementu Next lub `Exit For` instrukcji.

**Modyfikowanie kolekcji.** Obiekt modułu wyliczającego zwrócony przez <xref:System.Collections.IEnumerable.GetEnumerator%2A> zwykle nie pozwala na zmianę kolekcji poprzez dodanie, usunięcie, zastąpienie lub zmianę kolejności elementów. Jeśli po zainicjowaniu pętli `For Each`... `Next` zostanie zmieniona kolekcja, obiekt modułu wyliczającego jest nieprawidłowy, a kolejna próba uzyskania dostępu do elementu powoduje wyjątek <xref:System.InvalidOperationException>.

Jednak ten blok modyfikacji nie jest określany przez Visual Basic, ale raczej przez implementację interfejsu <xref:System.Collections.IEnumerable>. Możliwe jest wdrożenie `IEnumerable` w sposób umożliwiający modyfikację podczas iteracji. Jeśli rozważasz taką modyfikację dynamiczną, upewnij się, że rozumiesz charakterystykę implementacji `IEnumerable` w używanej kolekcji.

**Modyfikowanie elementów kolekcji.** Właściwość <xref:System.Collections.IEnumerator.Current%2A> obiektu Enumerator jest [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md)i zwraca lokalną kopię każdego elementu kolekcji. Oznacza to, że nie można modyfikować samych elementów w pętli `For Each`... `Next`. Wszelkie wprowadzone zmiany mają wpływ tylko na kopię lokalną z `Current` i nie zostaną odzwierciedlone w źródłowej kolekcji. Jeśli jednak element jest typem referencyjnym, można modyfikować członków wystąpienia, do którego wskazuje. Poniższy przykład modyfikuje składową `BackColor` każdego elementu `thisControl`. Nie można jednak modyfikować samego `thisControl`.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Poprzedni przykład może zmodyfikować składową `BackColor` każdego elementu `thisControl`, chociaż nie można modyfikować `thisControl`.

**Przechodzenie między tablicami.** Ponieważ Klasa <xref:System.Array> implementuje interfejs <xref:System.Collections.IEnumerable>, wszystkie tablice uwidaczniają metodę <xref:System.Array.GetEnumerator%2A>. Oznacza to, że można wykonać iterację tablicy z pętlą `For Each`... `Next`. Można jednak tylko odczytać elementy tablicy. Nie można ich zmienić.

## <a name="example"></a>Przykład

Poniższy przykład wyświetla listę wszystkich folderów w C:\ Katalog przy użyciu klasy <xref:System.IO.DirectoryInfo>.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje procedurę sortowania kolekcji. Przykład sortuje wystąpienia klasy `Car`, które są przechowywane w <xref:System.Collections.Generic.List%601>. Klasa `Car` implementuje interfejs <xref:System.IComparable%601>, który wymaga zaimplementowania metody <xref:System.IComparable%601.CompareTo%2A>.

Każde wywołanie metody <xref:System.IComparable%601.CompareTo%2A> wykonuje pojedyncze porównanie, które jest używane do sortowania. Kod pisany przez użytkownika w metodzie `CompareTo` zwraca wartość dla każdego porównania bieżącego obiektu z innym obiektem. Zwracana wartość jest mniejsza niż zero, jeśli bieżący obiekt jest mniejszy niż inny obiekt, większy niż zero, jeśli bieżący obiekt jest większy niż inny obiekt, i zero, jeśli są równe. Dzięki temu można zdefiniować w kodzie kryteria dla wartości większej niż, mniejszej niż i równej.

W metodzie `ListCars` instrukcja `cars.Sort()` sortuje listę. To wywołanie metody <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.List%601> powoduje automatyczne wywoływanie metody `CompareTo` dla obiektów `Car` w `List`.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Zobacz także

- [Kolekcje](../../../standard/collections/index.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- Inicjatory @no__t 0Object: Typy nazwane i anonimowe @ no__t-0
- [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
