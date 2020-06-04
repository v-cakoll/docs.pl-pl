---
title: Yield, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: cc89e6f9bc2ccb4fff9a9fe12cd190a6b2d212dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401371"
---
# <a name="yield-statement-visual-basic"></a>Yield — Instrukcja (Visual Basic)
Wysyła następny element kolekcji do `For Each...Next` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Parametry  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie, które jest niejawnie konwertowane na typ funkcji iteratora lub `Get` metody dostępu, która zawiera `Yield` instrukcję.|  
  
## <a name="remarks"></a>Uwagi  
 `Yield`Instrukcja zwraca jeden element kolekcji w danym momencie. `Yield`Instrukcja jest zawarta w funkcji iteratora lub `Get` metodzie dostępu, która wykonuje niestandardowe iteracje w kolekcji.  
  
 Używasz funkcji iteratora przy użyciu [for each... Następna instrukcja](for-each-next-statement.md) lub zapytanie LINQ. Każda iteracja `For Each` pętli wywołuje funkcję iteratora. Gdy `Yield` instrukcja zostanie osiągnięta w funkcji iteratora, `expression` jest zwracana, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Niejawna konwersja musi istnieć z typu `expression` w `Yield` instrukcji na zwracany typ iteratora.  
  
 Możesz użyć `Exit Function` instrukcji lub, `Return` Aby zakończyć iterację.  
  
 "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany w `Iterator` funkcji lub `Get` metodzie dostępu.  
  
 Aby uzyskać więcej informacji na temat funkcji iteratora i `Get` metod dostępu, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Funkcje iteratora i metody uzyskiwania dostępu  
 Deklaracja funkcji iteratora lub `Get` metody dostępu musi spełniać następujące wymagania:  
  
- Musi zawierać modyfikator [iteratora](../modifiers/iterator.md) .  
  
- Typem zwracanym musi być <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> ,, <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> .  
  
- Nie może mieć żadnych `ByRef` parametrów.  
  
 Nie można wykonać funkcji iteratora w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.  
  
 Funkcja iteratora może być funkcją anonimową. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 `Yield`Instrukcja może znajdować się wewnątrz `Try` bloku [try... Catch... Finally — instrukcja](try-catch-finally-statement.md). `Try`Blok, który ma `Yield` instrukcję, może mieć `Catch` bloki i może mieć `Finally` blok.  
  
 `Yield`Instrukcja nie może znajdować się wewnątrz `Catch` bloku lub `Finally` bloku.  
  
 Jeśli `For Each` treść (poza funkcją iteratora) zgłasza wyjątek, `Catch` blok w funkcji iteratora nie jest wykonywany, ale `Finally` jest wykonywany blok w funkcji iteratora. `Catch`Blok wewnątrz funkcji iteratora przechwytuje tylko wyjątki, które występują wewnątrz funkcji iteratora.  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Poniższy kod zwraca element `IEnumerable (Of String)` z funkcji iteratora, a następnie iteruje elementy `IEnumerable (Of String)` .  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Wywołanie `MyIteratorFunction` nie wykonuje treści funkcji. Zamiast tego wywołanie zwraca `IEnumerable(Of String)` `elements` zmienną.  
  
 W iteracji `For Each` pętli <xref:System.Collections.IEnumerator.MoveNext%2A> Metoda jest wywoływana dla `elements` . To wywołanie wykonuje treść `MyIteratorFunction` przed `Yield` osiągnięciem następnej instrukcji. `Yield`Instrukcja zwraca wyrażenie, które określa nie tylko wartość `element` zmiennej do użycia przez treść pętli, ale również <xref:System.Collections.Generic.IEnumerator%601.Current%2A> Właściwość elementów, która jest `IEnumerable (Of String)` .  
  
 W każdej kolejnej iteracji `For Each` pętli wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po osiągnięciu `Yield` instrukcji. `For Each`Pętla kończy się, gdy zostanie osiągnięty koniec funkcji iteratora lub `Return` `Exit Function` instrukcji lub.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](for-next-statement.md) pętla. Każda iteracja [dla każdej](for-each-next-statement.md) treści instrukcji w programie `Main` tworzy wywołanie `Power` funkcji iteratora. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcji, która występuje w następnej iteracji `For…Next` pętli.  
  
 Typem zwracanym metody iteratora jest <xref:System.Collections.Generic.IEnumerable%601> Typ interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje `Get` metodę dostępu, która jest iteratorem. Deklaracja właściwości zawiera `Iterator` modyfikator.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje](index.md)
