---
title: For Each...Next — Instrukcja (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 56
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1593d279d4338ebadca803fe757a201cbcd654b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
|`element`|Wymagane w `For Each` instrukcji. Opcjonalnie w `Next` instrukcji. Zmienna. Używany do iterowania po elementach kolekcji.|  
|`datatype`|Jeśli wymagane `element` nie jest już zadeklarowany. Typ danych `element`.|  
|`group`|Wymagana. Zmienna z typem jest typ kolekcji lub obiektu. Odwołuje się do kolekcji, w którym `statements` mają być powtarzany.|  
|`statements`|Opcjonalna. Co najmniej jeden instrukcji między `For Each` i `Next` uruchomionymi na każdym z elementów `group`.|  
|`Continue For`|Opcjonalna. Przekazuje sterowanie do początku `For Each` pętli.|  
|`Exit For`|Opcjonalna. Przekazuje sterowanie poza `For Each` pętli.|  
|`Next`|Wymagana. Kończy definicję `For Each` pętli.|  
  
## <a name="simple-example"></a>Prosty przykład  
 Użyj `For Each`... `Next` pętli, gdy ma zostać powtórzony zestaw instrukcji dla każdego elementu w kolekcji lub tablicy.  
  
> [!TIP]
>  A [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) działa również podczas skojarzyć każdej iteracji pętli z zmienna sterująca i określania wartości początkowe i końcowe dla tej zmiennej. Jednak gdy mamy do czynienia z kolekcją, pojęcie wartości początkowej i końcowej nie jest zrozumiały i użytkownik nie musi wiedzieć, ile elementów ma kolekcji. W przypadku tego rodzaju `For Each`... `Next` pętli jest często lepszym rozwiązaniem.  
  
 W poniższym przykładzie `For Each`...`Next` Instrukcja iterację wszystkie elementy kolekcji List.  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Aby uzyskać więcej przykładów, zobacz [kolekcje](../../../standard/collections/index.md) i [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Pętle zagnieżdżone  
 Można zagnieżdżać `For Each` pętle, ustawiając dla pętli w innym.  
  
 W poniższym przykładzie pokazano zagnieżdżonych `For Each`...`Next` struktury.  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Podczas zagnieżdżania pętle, każdej pętli musi mieć unikatową `element` zmiennej.  
  
 Można zagnieżdżać w różnych rodzajów struktury sterujące wewnątrz innych. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Zakończ dla i Kontynuuj dla  
 [Zakończyć dla](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcja powoduje wykonanie zakończyć `For`...`Next` pętli i transfer kontroli do instrukcji następującej `Next` instrukcji.  
  
 `Continue For` Instrukcji sterowania natychmiast przenosi do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [kontynuować instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Poniższy przykład przedstawia użycie `Continue For` i `Exit For` instrukcje.  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Można wprowadzić dowolną liczbę `Exit For` instrukcje w `For Each` pętli. Gdy jest używany w zagnieżdżonych `For Each` pętle, `Exit For` powoduje wykonanie zakończyć najbardziej kontroli pętli i przesyłania dalej wyższy poziom zagnieżdżenia.  
  
 `Exit For` często używane po dokonaniu oceny spełnienia określonego warunku, na przykład w `If`... `Then`... `Else` struktury. Możesz chcieć użyć `Exit For` następujące warunki:  
  
-   Kontynuowanie wykonania iteracji jest niepotrzebne lub niemożliwe. Może to być spowodowane Błędna wartość lub zakończenia żądania.  
  
-   Wystąpił wyjątek w `Try`... `Catch`... `Finally`. Można na przykład `Exit For` na końcu `Finally` bloku.  
  
-   Miejsca nieskończonej pętli, czyli pętli, które można uruchomić dużych lub nawet nieskończoną liczbę razy. W przypadku wykrycia takim stanie, można użyć `Exit For` wyjścia z pętli. Aby uzyskać więcej informacji, zobacz [czy... Pętla instrukcji](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Iteratory  
 Możesz użyć *iterator* nawiązał niestandardowych iteracji w kolekcji. Iterator może być funkcją lub `Get` dostępu. Używa `Yield` instrukcji, aby zwracany był każdy element kolekcji jednym naraz.  
  
 Należy wywołać przy użyciu iteratora `For Each...Next` instrukcji. Każdej iteracji `For Each` pętli wywołuje iteratora. Gdy `Yield` osiągnie iteracyjne, wyrażenia w instrukcji `Yield` instrukcji jest zwracany, i są przechowywane w bieżącej lokalizacji w kodzie. Wykonanie jest ponownie z tej lokalizacji iteratora jest wywoływana przy następnym uruchomieniu.  
  
 W poniższym przykładzie użyto funkcji iteracyjnej. Funkcja iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. W `ListEvenNumbers` metoda, każdej iteracji `For Each` treść instrukcji tworzy wywołanie funkcji iteracyjnej, który przechodzi do następnego `Yield` instrukcji.  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md), [instrukcji Yield](../../../visual-basic/language-reference/statements/yield-statement.md), i [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Gdy `For Each`...`Next` Uruchamia instrukcji, Visual Basic oblicza kolekcji tylko jeden raz, przed rozpoczęciem pętli. W przypadku zmiany z bloku instrukcji `element` lub `group`, zmiany te nie wpływają na iteracji pętli.  
  
 Gdy wszystkie elementy w kolekcji kolejno przypisane do `element`, `For Each` pętla zatrzymuje i kontrola przechodzi do instrukcji następującej `Next` instrukcji.  
  
 Jeśli `element` nie była zadeklarowana poza pętlę, należy ją zadeklarować w `For Each` instrukcji. Można zadeklarować typu `element` jawnie przy użyciu `As` instrukcji lub użytkownik może polegać na wnioskowanie o typie można przypisać do typu. W obu przypadkach zakres `element` jest treści pętli. Jednak nie można zadeklarować `element` zarówno poza i wewnątrz pętli.  
  
 Opcjonalnie można określić `element` w `Next` instrukcji. Poprawia czytelność z programem, zwłaszcza, jeśli można zagnieżdżać `For Each` pętli. Należy określić tę samą zmienną, która jest wyświetlana w polu `For Each` instrukcji.  
  
 Należy unikać zmiana wartości `element` wewnątrz pętli. W ten sposób można utrudnić do odczytywania i debugowanie kodu. Zmiana wartości `group` nie ma wpływu na kolekcji lub jej elementy, które zostały uznane za najpierw wprowadzenie pętli.  
  
 Gdy jest zagnieżdżanie pętli, jeśli `Next` instrukcji zewnętrzne poziom zagnieżdżenia napotkano przed `Next` wewnętrzny poziom kompilator sygnały wystąpił błąd. Jednak kompilator wykryć nakładających się błędu tylko w przypadku określenia `element` w każdym `Next` instrukcji.  
  
 Jeśli kod jest zależny od przechodzenie kolekcji w określonej kolejności `For Each`... `Next` pętli nie jest najlepszym rozwiązaniem, jeśli nie znasz właściwości obiektu modułu wyliczającego przedstawia kolekcji. Kolejność przechodzenie nie jest określana przez Visual Basic, ale przez <xref:System.Collections.IEnumerator.MoveNext%2A> metody obiektu modułu wyliczającego. W związku z tym nie można przewidzieć który element w kolekcji jest to pierwszy w `element`, lub który dalej do zwrócenia po danego elementu. Wydajność będzie bardziej niezawodny wyników przy użyciu struktury różnych pętli, takie jak `For`... `Next` lub `Do`... `Loop`.  
  
 Typ danych miary `element` musi być w taki sposób, że typ danych elementów `group` mogą być konwertowane do niego.  
  
 Typ danych miary `group` musi być typem referencyjnym, odnoszący się do kolekcji lub tablicy, która jest wyliczalny. Oznacza to, że najczęściej `group` odwołuje się do obiektu, który implementuje <xref:System.Collections.IEnumerable> interfejsu `System.Collections` przestrzeni nazw lub <xref:System.Collections.Generic.IEnumerable%601> interfejsu `System.Collections.Generic` przestrzeni nazw. `System.Collections.IEnumerable` definiuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody, która zwraca obiekt modułu wyliczającego dla kolekcji. Obiekt modułu wyliczającego implementuje `System.Collections.IEnumerator` interfejsu `System.Collections` przestrzeni nazw i udostępnia <xref:System.Collections.IEnumerator.Current%2A> właściwości i <xref:System.Collections.IEnumerator.Reset%2A> i <xref:System.Collections.IEnumerator.MoveNext%2A> metody. Visual Basic wykorzystuje te przechodzenie kolekcji.  
  
### <a name="narrowing-conversions"></a>Zawężanie konwersji  
 Gdy `Option Strict` ma ustawioną wartość `On`, konwersji zawężającej zazwyczaj powodują błędy kompilatora. W `For Each` instrukcji, jednak konwersje z elementów w `group` do `element` są oceniane i wykonywane w czasie wykonywania i błędy kompilatora spowodowane zawężanie konwersji są pomijane.  
  
 W poniższym przykładzie, przypisywanie `m` jako początkowa wartość `n` nie podczas kompilowania `Option Strict` znajduje się na, ponieważ konwersja `Long` do `Integer` jest konwersji zawężającej. W `For Each` instrukcji, jednak żaden błąd kompilatora jest zgłaszane, mimo że przypisanie do `number` wymaga tego samego konwersji z `Long` do `Integer`. W `For Each` występuje błąd czasu wykonywania instrukcji, która zawiera dużą liczbę, gdy <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> jest stosowany do dużą liczbą.  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>Wywołania IEnumerator  
 Podczas wykonywania `For Each`... `Next` rozpoczyna pętli, Visual Basic sprawdza, czy `group` odwołuje się do obiektu prawidłowej kolekcji. Jeśli nie, zgłasza wyjątek. W przeciwnym razie wywołuje <xref:System.Collections.IEnumerator.MoveNext%2A> — metoda i <xref:System.Collections.IEnumerator.Current%2A> właściwości obiektu modułu wyliczającego do zwrócenia pierwszego elementu. Jeśli `MoveNext` oznacza brak nie następnym elementem, oznacza to, jeśli kolekcja jest pusta, `For Each` pętla zatrzymuje i kontrola przechodzi do instrukcji następującej `Next` instrukcji. W przeciwnym razie ustawia Visual Basic `element` do pierwszego elementu i uruchamia blok instrukcji.  
  
 Po każdej aktualizacji Visual Basic napotka `Next` instrukcji, zwraca do `For Each` instrukcji. Ponownie wywołuje `MoveNext` i `Current` do zwrócenia z następnym elementem i ponownie uruchamia blok lub zatrzymuje pętli w zależności od wyniku. Ten proces jest kontynuowany do momentu `MoveNext` wskazuje nie następny element lub `Exit For` napotkano instrukcji.  
  
 **Modyfikowanie kolekcji.** Obiekt modułu wyliczającego zwrócony przez <xref:System.Collections.IEnumerable.GetEnumerator%2A> zwykle pozwala zmienić kolekcji przez dodawanie, usuwanie, zastępowanie lub zmianę kolejności elementów. W przypadku zmiany kolekcji po zainicjowaniu `For Each`... `Next` pętli, obiekt modułu wyliczającego staje się nieprawidłowa i powoduje, że następnej próbie uzyskania dostępu do elementu <xref:System.InvalidOperationException> wyjątku.  
  
 Jednak to blokowanie modyfikacji nie jest określany przez program Visual Basic, ale raczej przez implementację <xref:System.Collections.IEnumerable> interfejsu. Istnieje możliwość wykonania `IEnumerable` w sposób umożliwiający modyfikacji podczas iteracji. Planując wykonywania takich dynamicznych zmian, upewnij się, że rozumiesz właściwości `IEnumerable` implementacji na poziomie kolekcji używasz.  
  
 **Modyfikacja kolekcji elementów.** <xref:System.Collections.IEnumerator.Current%2A> Obiektu modułu wyliczającego jest [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md), i zwraca lokalną kopię każdego elementu w kolekcji. Oznacza to, że nie można zmodyfikować ze sobą elementy w `For Each`... `Next` pętli. Wszelkie zmiany wprowadzone wpływa na kopii lokalnej z `Current` i nie zostanie wprowadzona do kolekcji źródłowej. Jednak jeśli element jest typem referencyjnym, można zmodyfikować elementów członkowskich wystąpienia, na którą wskazuje. Poniższy przykład modyfikuje `BackColor` z każdej `thisControl` elementu. Nie można jednak zmienić `thisControl` samej siebie.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 Można zmodyfikować w poprzednim przykładzie `BackColor` z każdej `thisControl` elementu, mimo że nie można go zmodyfikować `thisControl` samej siebie.  
  
 **Przechodzenie przez tablic.** Ponieważ <xref:System.Array> klasa implementuje <xref:System.Collections.IEnumerable> interfejsu, wszystkie tablice ujawnia <xref:System.Array.GetEnumerator%2A> metody. Oznacza to, że można wykonać iterację tablicy o `For Each`... `Next` pętli. Można jednak tylko odczytać elementów tablicy. Nie można ich zmienić.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera listę wszystkich folderów w katalogu C:\ przy użyciu <xref:System.IO.DirectoryInfo> klasy.  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia procedurę sortowanie kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>. `Car` Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.  
  
 Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metoda pozwala jednym porównanie, które jest używane do sortowania. Napisany przez użytkownika kod `CompareTo` metoda zwraca wartość dla każdego porównania bieżący obiekt z innym obiektem. Wartość zwracana jest mniejsza niż zero, jeśli bieżący obiekt jest mniejsza od drugiego obiektu, większa niż zero, jeśli bieżący obiekt jest większy niż drugi obiekt i zero czy są równe. Dzięki temu można zdefiniować w kodzie kryteria większa niż poniżej, a równa.  
  
 W `ListCars` metody `cars.Sort()` instrukcji sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` wywoływanej automatycznie dla metody `Car` obiekty w `List`.  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje](../../../standard/collections/index.md)  
 [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Struktury pętli](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
