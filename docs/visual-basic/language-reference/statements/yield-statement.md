---
title: Yield — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 57b36bb32e1a575a645f7a15045bf0898dd10dfd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582216"
---
# <a name="yield-statement-visual-basic"></a>Yield — Instrukcja (Visual Basic)
Wysyła następny element kolekcji do instrukcji `For Each...Next`.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Parametry  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie, które jest niejawnie konwertowane na typ funkcji iteratora lub metody dostępu `Get`, która zawiera instrukcję `Yield`.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Yield` zwraca jeden element kolekcji w danym momencie. Instrukcja `Yield` jest zawarta w funkcji iteratora lub metodzie dostępu `Get`, która wykonuje niestandardowe iteracje w kolekcji.  
  
 Używasz funkcji iteratora przy użyciu [for each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md) lub zapytanie LINQ. Każda iteracja pętli `For Each` wywołuje funkcję iteratora. Po osiągnięciu instrukcji `Yield` w funkcji iteratora zwracana jest wartość `expression`, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Niejawna konwersja musi istnieć na podstawie typu `expression` w instrukcji `Yield` do zwracanego typu iteratora.  
  
 Aby zakończyć iterację, można użyć instrukcji `Exit Function` lub `Return`.  
  
 "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany w funkcji `Iterator` lub metodzie dostępu `Get`.  
  
 Aby uzyskać więcej informacji na temat funkcji iteratora i metod dostępu `Get`, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Funkcje iteratora i metody uzyskiwania dostępu  
 Deklaracja funkcji iteratora lub metody dostępu `Get` musi spełniać następujące wymagania:  
  
- Musi zawierać modyfikator [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md) .  
  
- Typem zwracanym musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
- Nie może mieć żadnych parametrów `ByRef`.  
  
 Nie można wykonać funkcji iteratora w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.  
  
 Funkcja iteratora może być funkcją anonimową. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 Instrukcja `Yield` może znajdować się wewnątrz bloku `Try` [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Blok `Try`, który zawiera instrukcję `Yield` może mieć `Catch` bloków i może mieć blok `Finally`.  
  
 Instrukcja `Yield` nie może znajdować się wewnątrz bloku `Catch` lub bloku `Finally`.  
  
 Jeśli treść `For Each` (poza funkcją iteratora) zgłasza wyjątek, blok `Catch` w funkcji iteratora nie zostanie wykonany, ale jest wykonywany blok `Finally` w funkcji iteratora. Blok `Catch` wewnątrz funkcji iteratora przechwytuje tylko wyjątki występujące wewnątrz funkcji iteratora.  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Poniższy kod zwraca `IEnumerable (Of String)` z funkcji iteratora, a następnie iteruje elementy `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Wywołanie `MyIteratorFunction` nie wykonuje treści funkcji. Zamiast tego wywołanie zwraca `IEnumerable(Of String)` do zmiennej `elements`.  
  
 W przypadku iteracji pętli `For Each` Metoda <xref:System.Collections.IEnumerator.MoveNext%2A> jest wywoływana dla `elements`. To wywołanie wykonuje treść `MyIteratorFunction` do momentu osiągnięcia następnej instrukcji `Yield`. Instrukcja `Yield` zwraca wyrażenie, które określa nie tylko wartość zmiennej `element` do użycia przez treść pętli, ale również właściwość <xref:System.Collections.Generic.IEnumerator%601.Current%2A> elementów, która jest `IEnumerable (Of String)`.  
  
 W każdej kolejnej iteracji pętli `For Each` wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, i ponownie zatrzymywane, gdy dociera do instrukcji `Yield`. Pętla `For Each` kończy się, gdy zostanie osiągnięty koniec funkcji iteratora lub `Return` lub `Exit Function`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera instrukcję `Yield`, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. Każda iteracja [dla każdej](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treści instrukcji w `Main` tworzy wywołanie funkcji iteratora `Power`. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania instrukcji `Yield`, która występuje w następnej iteracji pętli `For…Next`.  
  
 Zwracany typ metody iteratora to <xref:System.Collections.Generic.IEnumerable%601>, typ interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład demonstruje metodę dostępu `Get`, która jest iteratorem. Deklaracja właściwości zawiera modyfikator `Iterator`.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje](../../../visual-basic/language-reference/statements/index.md)
