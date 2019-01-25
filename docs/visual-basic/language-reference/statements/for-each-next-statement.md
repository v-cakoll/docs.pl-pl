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
ms.openlocfilehash: a44aff8407a29ef7f3712e116301cfce0aa984ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700432"
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
|`group`|Wymagana. Zmienna typu, który jest typem kolekcji lub obiektu. Odnosi się do kolekcji, nad którym `statements` ma zostać powtórzony.|  
|`statements`|Opcjonalna. Jedna lub więcej instrukcji między `For Each` i `Next` uruchamianą w każdym elemencie `group`.|  
|`Continue For`|Opcjonalna. Przekazuje sterowanie do początku `For Each` pętli.|  
|`Exit For`|Opcjonalna. Przekazuje sterowanie poza `For Each` pętli.|  
|`Next`|Wymagana. Kończy definicję `For Each` pętli.|  
  
## <a name="simple-example"></a>Prosty przykład  
 Użyj `For Each`... `Next` pętli, gdy chcesz powtórzyć zestaw instrukcji dla każdego elementu w kolekcji lub tablicy.  
  
> [!TIP]
>  Element [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) działa dobrze podczas kojarzenia każdej iteracji pętli z zmienna sterująca i określić wartości początkowe i końcowe dla tej zmiennej. Jednak masz do czynienia z kolekcją, koncepcji początkowych i końcowych wartości nie jest istotne, gdy użytkownik nie musi wiedzieć, ile elementów ma kolekcję. W tym przypadku `For Each`... `Next` pętli często jest lepszym rozwiązaniem.  
  
 W poniższym przykładzie `For Each`...`Next` instrukcja wykonuje iterację przez wszystkie elementy kolekcji listy.  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Aby uzyskać więcej przykładów, zobacz [kolekcje](../../../standard/collections/index.md) i [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Pętle zagnieżdżone  
 Można zagnieżdżać `For Each` pętli przez umieszczenie pętli w innym.  
  
 W poniższym przykładzie pokazano zagnieżdżonych `For Each`...`Next` struktury.  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Zagnieżdżanie pętli każdej pętli musi mieć unikatową `element` zmiennej.  
  
 Można także zagnieżdżać różne rodzaje struktur sterujących wewnątrz innych. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Zakończ dla i Kontynuuj dla  
 [Wyjść dla](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcja powoduje wykonanie zakończyć działanie `For`...`Next` pętli i transfer kontroli do kolejnej instrukcji `Next` instrukcji.  
  
 `Continue For` Instrukcji sterowania natychmiast przenosi do następnej iteracji pętli. Aby uzyskać więcej informacji, zobacz [nadal instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Poniższy przykład pokazuje, jak używać `Continue For` i `Exit For` instrukcji.  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Można umieścić dowolną liczbę `Exit For` instrukcji w `For Each` pętli. Gdy jest używana w ramach zagnieżdżonych `For Each` pętli, `Exit For` powoduje wykonanie zakończyć działanie najbardziej wewnętrznej kontroli pętli i przekazywania dalej wyższy poziom zagnieżdżenia.  
  
 `Exit For` jest często używana po dokonaniu oceny jakiś warunek, na przykład w `If`... `Then`... `Else` struktury. Możesz chcieć użyć `Exit For` następujące warunki:  
  
-   Iterowanie w dalszym ciągu jest niepotrzebne lub wręcz niemożliwe. Może to być spowodowane błędną wartość lub żądanie zakończenia działania.  
  
-   Wystąpił wyjątek `Try`... `Catch`... `Finally`. Można na przykład `Exit For` na końcu `Finally` bloku.  
  
-   Tam nieskończonej pętli, czyli pętlę, która może działać dużych lub nawet nieskończona liczba prób. Jeśli zostaną wykryte tych warunków, można użyć `Exit For` jako znak ucieczki dla pętli. Aby uzyskać więcej informacji, zobacz [zrobić... Instrukcja pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Iteratory  
 Możesz użyć *iteratora* do wykonywania niestandardowych iteracji przez kolekcję. Iterator może być funkcją lub `Get` metody dostępu. Używa ona `Yield` instrukcja zwraca każdy element kolekcji naraz.  
  
 Wywołujesz iterację używając `For Each...Next` instrukcji. Każda iteracja `For Each` pętli wywołuje iteratora. Gdy `Yield` osiągnięciu instrukcji w iteratorze, wyrażenie w `Yield` instrukcji jest zwracane, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji w przy następnym wywołaniu iteratora.  
  
 W poniższym przykładzie użyto funkcji iteratora. Funkcja iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. W `ListEvenNumbers` metody, każda iteracja `For Each` treść instrukcji tworzy wywołanie funkcji iteratora, który przechodzi do następnej `Yield` instrukcji.  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md), [instrukcji Yield](../../../visual-basic/language-reference/statements/yield-statement.md), i [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Gdy `For Each`...`Next` Uruchamia instrukcję, Visual Basic ocenia kolekcji tylko jeden raz, przed rozpoczęciem pętli. Jeśli zmiany z bloku instrukcji `element` lub `group`, zmiany te nie wpływają na iteracji pętli.  
  
 Gdy wszystkie elementy w kolekcji kolejno przypisane do `element`, `For Each` pętla zatrzymuje i kontrola przechodzi do instrukcji następującej `Next` instrukcji.  
  
 Jeśli `element` nie była zadeklarowana poza pętlę, należy zadeklarować ją w `For Each` instrukcji. Możesz deklarować typ `element` jawnie przy użyciu `As` instrukcji lub możesz polegać na wnioskowanie o typie, aby przypisać typu. W obu przypadkach zakres `element` treść pętli. Jednak nie można zadeklarować `element` zarówno na zewnątrz i wewnątrz pętli.  
  
 Opcjonalnie możesz określić `element` w `Next` instrukcji. To zwiększa czytelność program, zwłaszcza, jeśli można zagnieżdżać `For Each` pętli. Należy określić tę samą zmienną, która pojawia się w odpowiednich `For Each` instrukcji.  
  
 Można uniknąć, zmieniając wartość ciągu `element` wewnątrz pętli. W ten sposób może utrudnić do odczytywania i debugowania kodu. Zmiana wartości `group` nie ma wpływu na kolekcji lub jego elementy, które zostały określone, jeśli pętla została najpierw wprowadzona.  
  
 Gdy jesteś zagnieżdżania pętli, jeśli `Next` instrukcji zewnętrzne poziom zagnieżdżenia zostanie osiągnięty zanim `Next` wewnętrzny poziomu, kompilator sygnalizuje błąd. Jednak kompilator to wykryć nakładających się błąd, tylko wtedy, gdy należy określić `element` w każdym `Next` instrukcji.  
  
 Jeśli Twój kod jest zależna od przechodzenie kolekcji w określonej kolejności `For Each`... `Next` pętli nie jest najlepszym wyborem, jeśli nie znasz cechy obiekt modułu wyliczającego udostępnia kolekcji. Kolejność przechodzenia nie jest ustalany na podstawie języka Visual Basic, ale przez <xref:System.Collections.IEnumerator.MoveNext%2A> metody obiektu modułu wyliczającego. W związku z tym, nie można przewidzieć, który element w kolekcji jest pierwszym, który ma zostać zwrócone w `element`, lub który jest dalej do zwrócenia po dany element. Może osiągnąć bardziej niezawodne wyników przy użyciu struktury pętli różnych, takich jak `For`... `Next` lub `Do`... `Loop`.  
  
 Typ danych `element` musi być w taki sposób, że typ danych elementów `group` mogą być konwertowane do niego.  
  
 Typ danych `group` musi być typem referencyjnym, który odwołuje się do kolekcji lub tablicy, która jest wyliczalna. Oznacza to, że najczęściej `group` odwołuje się do obiektu, który implementuje <xref:System.Collections.IEnumerable> interfejsu `System.Collections` przestrzeni nazw lub <xref:System.Collections.Generic.IEnumerable%601> interfejsu `System.Collections.Generic` przestrzeni nazw. `System.Collections.IEnumerable` definiuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody, która zwraca obiekt modułu wyliczającego dla kolekcji. Obiekt modułu wyliczającego implementuje `System.Collections.IEnumerator` interfejsu `System.Collections` przestrzeni nazw i udostępnia <xref:System.Collections.IEnumerator.Current%2A> właściwości i <xref:System.Collections.IEnumerator.Reset%2A> i <xref:System.Collections.IEnumerator.MoveNext%2A> metody. Visual Basic używa ich do przenoszenia kolekcji.  
  
### <a name="narrowing-conversions"></a>Konwersje zawężające  
 Gdy `Option Strict` ustawiono `On`, konwersje zawężające zazwyczaj powodują błędy kompilatora. W `For Each` instrukcji, jednak konwersje z elementów w `group` do `element` są obliczane i wykonywane w czasie wykonywania oraz błędów kompilatora spowodowanych przez zawężających są pomijane.  
  
 W poniższym przykładzie przypisanie `m` jako wartość początkową dla `n` nie podczas kompilowania `Option Strict` jest włączony, ponieważ konwersja `Long` do `Integer` jest konwersją zawężającą. W `For Each` instrukcji, błąd kompilatora nie jest jednak zgłoszone, nawet jeśli przypisanie do `number` wymaga tych samych konwersja `Long` do `Integer`. W `For Each` wystąpi błąd czasu wykonywania instrukcji, która zawiera dużą liczbą, gdy <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> jest stosowany do dużą liczbą.  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>IEnumerator wywołania  
 Podczas wykonywania `For Each`... `Next` rozpoczyna pętli, Visual Basic — sprawdza, czy `group` odwołuje się do obiektu prawidłową kolekcję. W przeciwnym razie występuje wyjątek. W przeciwnym razie wywoływanych przez nią <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Current%2A> właściwości obiektu modułu wyliczającego, aby powrócić do pierwszego elementu. Jeśli `MoveNext` wskazuje, że nie ma żadnego elementu dalej, oznacza to, jeśli kolekcja jest pusta, `For Each` pętla zatrzymuje i kontrola przechodzi do instrukcji następującej `Next` instrukcji. W przeciwnym wypadku ustawia języka Visual Basic `element` do pierwszego elementu i uruchamia blok instrukcji.  
  
 Każdym języka Visual Basic napotyka `Next` instrukcja zwraca do `For Each` instrukcji. Ponownie wywołuje `MoveNext` i `Current` do zwrócenia następnego elementu i ponownie uruchamia blok albo zatrzymuje pętli w zależności od wyniku. Ten proces jest kontynuowany do momentu `MoveNext` wskazuje, że nie ma żadnego elementu dalej lub `Exit For` napotkania instrukcji.  
  
 **Modyfikowanie kolekcji.** Obiekt modułu wyliczającego zwrócony przez <xref:System.Collections.IEnumerable.GetEnumerator%2A> zwykle nie pozwala zmienić kolekcję poprzez dodawanie, usuwanie, zastępowanie lub zmiany kolejności elementów. Jeśli zmienisz kolekcji po zainicjowaniu `For Each`... `Next` pętli, obiekt modułu wyliczającego staje się nieprawidłowy i powoduje, że następnej próbie uzyskania dostępu do elementu <xref:System.InvalidOperationException> wyjątku.  
  
 Jednak to blokowanie modyfikacji nie jest określana przez program Visual Basic, ale raczej przez implementację <xref:System.Collections.IEnumerable> interfejsu. Istnieje możliwość zaimplementowania `IEnumerable` w sposób, który umożliwia modyfikowanie podczas iteracji. Jeśli rozważasz, wykonując takie dynamicznych modyfikacji, upewnij się, że zrozumieć charakterystyki `IEnumerable` implementacji zbierania używasz.  
  
 **Modyfikowanie elementów kolekcji.** <xref:System.Collections.IEnumerator.Current%2A> Właściwość obiekt modułu wyliczającego jest [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md), i zwraca kopię lokalną każdego elementu kolekcji. Oznacza to, że nie można zmodyfikować samych elementów w `For Each`... `Next` pętli. Wszelkie zmiany wprowadzone dotyczy tylko kopia lokalna z `Current` i nie zostanie wprowadzona do podstawowej kolekcji. Jednak jeśli element jest typem referencyjnym, można zmodyfikować składowych wystąpienia, na który wskazuje. Poniższy przykład modyfikuje `BackColor` z każdej `thisControl` elementu. Nie można jednak zmodyfikować `thisControl` sam.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 Poprzedni przykład można zmodyfikować `BackColor` z każdej `thisControl` elementu, mimo że nie można go zmodyfikować `thisControl` sam.  
  
 **Przechodzenie przez tablic.** Ponieważ <xref:System.Array> klasy implementuje <xref:System.Collections.IEnumerable> uwidaczniać wszystkie tablice interfejsu <xref:System.Array.GetEnumerator%2A> metody. Oznacza to, że można wykonać iterację tablicy o liczbie `For Each`... `Next` pętli. Jednak mogą odczytywać tylko elementy tablicy. Nie można ich zmienić.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wyświetla listę wszystkich folderów w katalogu C:\ przy użyciu <xref:System.IO.DirectoryInfo> klasy.  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykładową procedurę sortowania zbioru. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>. `Car` Klasy implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.  
  
 Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody tworzy pojedyncze porównanie, który jest używane do sortowania. Kod napisany przez użytkownika w `CompareTo` metoda zwraca wartość dla każdego porównania bieżącego obiektu z innego obiektu. Wartość zwracana jest mniejsza niż zero, jeżeli bieżący obiekt jest mniejszy niż inny obiekt, większa niż zero, jeśli bieżący obiekt jest większy niż inny obiekt i zero czy są równe. Umożliwia to definiowanie w kodzie kryteriów dla większych niż, mniejsze więc równa.  
  
 W `ListCars` metody `cars.Sort()` instrukcji sortuje listy. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` metoda zostaje wywołana automatycznie dla `Car` obiekty w `List`.  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
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
