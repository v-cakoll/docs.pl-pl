---
title: Operacje na zestawie (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5b546d9df8752fd7afd6e0db4525bc923a74bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-c"></a>Operacje na zestawie (C#)
Operacje na zestawie w składniku LINQ odwoływać się do operacji zapytania, które wywołują zestaw wyników, który jest oparty na obecności lub braku równoważne elementów w obrębie tego samego lub oddzielne kolekcje (lub zestawy).  
  
 Metody operator standardowe zapytań, które wykonują operacje na zestawie są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Usuwa zduplikowane wartości z kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Z wyjątkiem|Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie są widoczne w druga kolekcja.|Nie dotyczy.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|INTERSECT|Zwraca część wspólną zestawu, co oznacza elementy, które są wyświetlane w każdym z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Union|Zwraca zestaw, co oznacza unikatowych elementów, które pojawiają się w jednym z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porównanie operacje na zestawie  
  
### <a name="distinct"></a>Distinct  
 Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody w sekwencji znaków. Zwrócony sekwencja zawiera elementy unikatowe z sekwencji wejściowych.  
  
 ![Grafika przedstawiająca zachowanie Distinct &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Różne")  
  
### <a name="except"></a>Z wyjątkiem  
 Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Zwrócony sekwencja zawiera tylko elementy z pierwszego sekwencji wejściowych, które nie znajdują się w drugim sekwencji wejściowych.  
  
 ![Grafika przedstawiająca działania z wyjątkiem &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "z wyjątkiem")  
  
### <a name="intersect"></a>INTERSECT  
 Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Zwrócony sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca część wspólną dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>Union  
 Na poniższej ilustracji przedstawiono Unii operacji na dwóch sekwencji znaków. Zwrócony sekwencja zawiera elementy unikatowe z obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca złożenie dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Unii")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Porady: łączenie i porównywanie kolekcji ciągów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
