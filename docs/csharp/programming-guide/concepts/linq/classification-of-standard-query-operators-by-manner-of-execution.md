---
title: Klasyfikacja standardowych operatorów zapytań według sposobu wykonania (C#)
ms.date: 07/20/2015
ms.assetid: b9435ce5-a7cf-4182-9f01-f3468a5533dc
ms.openlocfilehash: ccf8fced5c92ceaaf84f9240e235da0e2b56ac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924292"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-c"></a>Klasyfikacja standardowych operatorów zapytań według sposobu wykonania (C#)
Implementacje LINQ do obiektów standardowych metod operatora kwerendy są wykonywane w jeden z dwóch głównych sposobów: natychmiastowe lub odroczone. Operatory zapytań, które używają odroczonego wykonania można dodatkowo podzielić na dwie kategorie: przesyłanie strumieniowe i nieprzesyłania strumieniowego. Jeśli wiesz, jak różne operatory kwerend y wykonać, może pomóc zrozumieć wyniki, które można uzyskać z danej kwerendy. Jest to szczególnie ważne, jeśli źródło danych się zmienia lub jeśli budujesz kwerendę na podstawie innej kwerendy. W tym temacie klasyfikuje operatorów standardowych zapytań zgodnie z ich sposobem wykonywania.  
  
## <a name="manners-of-execution"></a>Maniery wykonania  
  
### <a name="immediate"></a>Natychmiastowe  
 Natychmiastowe wykonanie oznacza, że źródło danych jest odczytywane, a operacja jest wykonywana w punkcie w kodzie, w którym jest zadeklarowana kwerenda. Wszystkie standardowe operatory zapytań, które zwracają pojedynczy, niewyliczony wynik, są wykonywane natychmiast.  
  
### <a name="deferred"></a>Odroczonego  
 Odroczone wykonanie oznacza, że operacja nie jest wykonywana w punkcie w kodzie, w którym jest zadeklarowana kwerenda. Operacja jest wykonywana tylko wtedy, gdy zmienna kwerendy jest `foreach` wyliczana, na przykład przy użyciu instrukcji. Oznacza to, że wyniki wykonywania kwerendy zależą od zawartości źródła danych, gdy kwerenda jest wykonywana, a nie po zdefiniowaniu kwerendy. Jeśli zmienna kwerendy jest wyliczana wiele razy, wyniki mogą się różnić za każdym razem. Prawie wszystkie standardowe operatory zapytań, których typ zwracany jest <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IOrderedEnumerable%601> wykonać w sposób odroczony.  
  
 Operatory zapytań, które używają odroczonego wykonania można dodatkowo sklasyfikować jako przesyłanie strumieniowe lub nieprzesyłania strumieniowego.  
  
#### <a name="streaming"></a>Przesyłanie strumieniowe  
 Operatory przesyłania strumieniowego nie muszą odczytywać wszystkich danych źródłowych, zanim wydadzą elementy. W czasie wykonywania operator przesyłania strumieniowego wykonuje swoją operację na każdym elemencie źródłowym, ponieważ jest odczytywany i daje element, jeśli jest to właściwe. Operator przesyłania strumieniowego kontynuuje odczytywanie elementów źródłowych, dopóki nie zostanie wyprodukowany element wynikowy. Oznacza to, że więcej niż jeden element źródłowy może być odczytywany w celu uzyskania jednego elementu wynikowego.  
  
#### <a name="non-streaming"></a>Brak przesyłania strumieniowego  
 Operatory nieprzesyłate strumieniowo muszą odczytać wszystkie dane źródłowe, zanim mogą udawać element wynikowy. Operacje, takie jak sortowanie lub grupowanie należą do tej kategorii. W czasie wykonywania operatory zapytań nieprzesyłających strumieniowo odczytać wszystkie dane źródłowe, umieścić go w strukturze danych, wykonać operację i przynieść wynikowe elementy.  
  
## <a name="classification-table"></a>Tabela klasyfikacji  
 W poniższej tabeli klasyfikuje każdą metodę operatora zapytań standardowych zgodnie z jej metodą wykonywania.  
  
> [!NOTE]
> Jeśli operator jest oznaczony w dwóch kolumnach, dwie sekwencje wejściowe są zaangażowane w operację, a każda sekwencja jest oceniana inaczej. W takich przypadkach jest zawsze pierwsza sekwencja na liście parametrów, która jest oceniana w sposób odroczonego, przesyłania strumieniowego.  
  
|Standardowy operator kwerendy|Typ zwracany|Natychmiastowe wykonanie|Odroczone wykonywanie przesyłania strumieniowego|Odroczone wykonanie bez przesyłania strumieniowego|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|Tsource|X|||  
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
|<xref:System.Linq.Enumerable.ElementAt%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|Tsource|X|||  
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
|<xref:System.Linq.Enumerable.Single%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|Tsource|X|||  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Składnia wyrażenia kwerendy dla standardowych operatorów kwerend (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [LINQ do obiektów (C#)](./linq-to-objects.md)
