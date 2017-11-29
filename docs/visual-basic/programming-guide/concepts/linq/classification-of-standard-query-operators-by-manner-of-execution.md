---
title: "Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 553a638cdaaebeaa5ab21850250b2d70536f557c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)
LINQ do obiektów implementacje metody — operator zapytań standardowe wykonania w jednym z dwóch sposobów głównego: odejścia. Operatory zapytań, które używają odroczonego wykonania można dodatkowo podzielić na dwie kategorie: przesyłanie strumieniowe i strumieniowo. Jeśli wiesz, jak wykonać operatory inne zapytanie, jego może ułatwić zrozumienie wyników, które można uzyskać z określonego zapytania. Jest to szczególnie istotne, jeśli źródło danych jest zmiana lub jeśli tworzysz zapytania na inne zapytanie. W tym temacie klasyfikuje standardowych operatorów zapytań zgodnie z ich sposób wykonywania.  
  
## <a name="manners-of-execution"></a>Sposobów wykonywania  
  
### <a name="immediate"></a>Natychmiastowe  
 Wykonanie natychmiastowe oznacza, że źródło danych jest do odczytu, a operacja jest wykonywana w momencie w kodzie, gdzie zapytanie jest zadeklarowany. Wszystkie standardowe operatory zapytań zwracających pojedynczą, wyliczalny wynik wykonania natychmiast.  
  
### <a name="deferred"></a>Odroczone  
 Wykonanie odroczone oznacza to, czy operacja nie jest wykonywana w momencie w kodzie gdzie zapytanie jest zadeklarowany. Operacja jest wykonywana tylko wtedy, gdy wyliczone zmienną zapytania, na przykład za pomocą `For Each` instrukcji. Oznacza to, że wyniki wykonywania zapytania zależy od zawartości źródła danych podczas wykonywania zapytania zamiast kiedy zdefiniowano zapytania. Jeśli do zmiennej zapytania jest wyliczyć wiele razy, wyniki mogą być inne zawsze. Prawie wszystkie standardowe operatory zapytań o typie zwracanym <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IOrderedEnumerable%601> w sposób opóźnieniem.  
  
 Operatory zapytań, które używają odroczonego wykonania można ponadto klasyfikowane jako przesyłania strumieniowego lub strumieniowo.  
  
#### <a name="streaming"></a>przesyłanie strumieniowe  
 Operatory przesyłania strumieniowego nie trzeba przed dają one elementy przeczytać źródło danych. W czasie wykonywania operator przesyłania strumieniowego wykonuje jego działanie dla każdego elementu źródłowego, ponieważ jest do odczytu i daje w wyniku elementu, jeśli są one. Operator przesyłania strumieniowego w dalszym ciągu odczytu elementy źródłowe, dopóki nie może być wywołany element wynik. Oznacza to, że więcej niż jeden element źródłowy może przeczytać wygenerowało jeden element wynik.  
  
#### <a name="non-streaming"></a>Strumieniowo  
 Operatory przesyłania strumieniowego nie musi odczytu źródło danych, przed dają one element wynik. Operacje takie jak sortowania lub grupowania należą do tej kategorii. W czasie wykonywania strumieniowo operatorów zapytań odczytywać źródło danych, poddane to struktura danych do operacji i uzyskanie wynikowych elementów.  
  
## <a name="classification-table"></a>Tabela klasyfikacji  
 Poniższa tabela klasyfikuje każdej metody operator standardowej kwerendy poprzez sposób wykonywania.  
  
> [!NOTE]
>  Jeśli operator jest oznaczony w dwóch kolumnach, dwóch sekwencji wejściowych są zaangażowane w operacji i poszczególnych sekwencji jest obliczane w inny sposób. W takich przypadkach jest zawsze sekwencja pierwszy na liście parametrów, które jest oceniane w odroczonego, przesyłanie strumieniowe sposób.  
  
|Operator zapytania standardowe|Zwracany typ|Natychmiastowe wykonanie|Wykonanie odroczone przesyłania strumieniowego|Odroczone strumieniowo wykonywania|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|Pojedynczą wartość numeryczną|X|||  
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
|<xref:System.Linq.Enumerable.Max%2A>|Pojedynczą wartość numeryczną, TSource lub TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|Pojedynczą wartość numeryczną, TSource lub TResult|X|||  
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
|<xref:System.Linq.Enumerable.Sum%2A>|Pojedynczą wartość numeryczną|X|||  
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
 <xref:System.Linq.Enumerable>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
