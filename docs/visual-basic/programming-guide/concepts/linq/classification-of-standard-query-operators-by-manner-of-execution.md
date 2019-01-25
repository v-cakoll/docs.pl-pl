---
title: Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
ms.openlocfilehash: 5e4204c3fa80acced42649e76abfa2be05f35d82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595178"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)
LINQ do obiektów implementacje metod standardowych operatorów zapytań wykonania w jednym z dwa główne sposoby: odejścia. Operatory zapytań, które używają odroczonego wykonania można dodatkowo podzielić na dwie kategorie: przesyłanie strumieniowe i obsługiwane strumieniowo. Jeśli wiesz, jak wykonać operatory inne zapytanie, jego może ułatwić zrozumienie wyników, które otrzymasz od określonego zapytania. Jest to szczególnie istotne, jeśli zmienia się ze źródłem danych lub jeśli tworzysz kwerendy na podstawie innego zapytania. W tym temacie klasyfikuje standardowych operatorów zapytań zgodnie z ich sposób działania.  
  
## <a name="manners-of-execution"></a>Sposobów wykonania  
  
### <a name="immediate"></a>Natychmiastowe  
 Natychmiastowe wykonanie oznacza, że źródło danych jest do odczytu, a operacja jest wykonywana w punkcie w kodzie, którym zadeklarowano zapytania. Wszystkie standardowe operatory zapytań, które zwracają wynik pojedynczy, wyliczalny wykonywane natychmiast.  
  
### <a name="deferred"></a>Odroczone  
 Wykonanie odroczone oznacza to, czy operacja nie jest wykonywane w punkcie w kodzie którym zadeklarowano zapytania. Operacja jest wykonywana tylko wtedy, gdy zmienna zapytania są wyliczane na przykład za pomocą `For Each` instrukcji. Oznacza to, że wyników wykonywania zapytania zależy od zawartości źródła danych, gdy zapytanie jest wykonywane, a nie gdy zdefiniowano zapytanie. Jeśli zmienna zapytania są wyliczane wiele razy, wyniki mogą się różnić z każdym razem, gdy. Prawie wszystkie standardowe operatory zapytań o zwracanym typie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IOrderedEnumerable%601> w sposób odroczone.  
  
 Operatorów zapytań, które używają odroczonego wykonania mogą być dodatkowo klasyfikowane jako przesyłania strumieniowego lub -streaming.  
  
#### <a name="streaming"></a>Przesyłanie strumieniowe  
 Operatory przesyłania strumieniowego jest konieczne odczytywać wszystkie dane źródłowego, przed dają one elementy. W czasie wykonywania przesyłania strumieniowego operator wykonuje jego działania dla każdego elementu źródłowego podczas odczytu i daje w wyniku elementu, jeśli jest to odpowiednie. Operator przesyłania strumieniowego w dalszym ciągu odczytywać elementy źródłowe, dopóki nie może wygenerować elementu wynik. Oznacza to, że więcej niż jeden element źródłowy może przeczytać do wyprodukowania jednego elementu wynik.  
  
#### <a name="non-streaming"></a>Obsługiwane strumieniowo  
 Operatory nie obsługiwane strumieniowo nie musi odczytywać wszystkie dane źródłowego, przed dają one elementu wynik. Operacje, takie jak sortowania i grupowania należą do tej kategorii. W czasie wykonywania operatory obsługiwane strumieniowo zapytań odczytywać wszystkie dane źródłowego, umieść struktury danych, do operacji i uzyskanie wynikowe elementy.  
  
## <a name="classification-table"></a>Tabela klasyfikacji  
 Poniższa tabela klasyfikuje każdej metody standardowej kwerendy operatora, zgodnie z jego metody wykonywania.  
  
> [!NOTE]
>  Jeśli operator jest oznaczony w dwóch kolumnach, dwóch sekwencji wejściowych biorących udział w operacji, a każda sekwencja jest obliczane inaczej. W takich przypadkach jest zawsze pierwszej sekwencji na liście parametrów, które jest obliczane w odroczonego, przesyłanie strumieniowe sposób.  
  
|Standardowego operatora zapytania|Zwracany typ|Natychmiastowe wykonanie|Wykonanie odroczone przesyłania strumieniowego|Odroczone obsługiwane strumieniowo wykonywania|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|Pojedyncza wartość liczbowa|X|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A>|Pojedyncza wartość liczbowa, TSource lub TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|Pojedyncza wartość liczbowa, TSource lub TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A>|Pojedyncza wartość liczbowa|X|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A>|Tablica TSource|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq.Enumerable>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
