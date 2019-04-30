---
title: Operacje na zestawie (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 9e507bbaa39bf040a8ce1564630fb5fbb8c0dbe4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712216"
---
# <a name="set-operations-c"></a>Operacje na zestawie (C#)
Operacje na zestawie w składniku LINQ dotyczą operacje zapytań, które tworzą zestaw wyników, który zależy od obecności lub braku równoważne elementów w obrębie tego samego lub oddzielne kolekcje (lub zestawy).  
  
 Metody standardowego operatora zapytań, które wykonują operacje na zestawie są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Usuwa zduplikowane wartości z kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Z wyjątkiem|Zwraca różnicę zestawu, który oznacza, że elementy jednej kolekcji, które nie są wyświetlane w drugiej kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|INTERSECT|Zwraca część wspólną zestawu, co oznacza, elementy, które są wyświetlane w każdym dwie kolekcje.|Nie dotyczy.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Union|Zwraca Unię zestawu, co oznacza unikatowych elementów, które pojawiają się w jednej z dwóch kolekcjach.|Nie dotyczy.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porównanie operacje na zestawie  
  
### <a name="distinct"></a>Distinct  
 Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody w sekwencji znaków. Zwracana sekwencja zawiera unikatowych elementów z sekwencji wejściowych.  
  
 ![Grafika przedstawiająca zachowanie słowa kluczowego DISTINCT&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a>Z wyjątkiem  
 Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowych, które nie znajdują się w drugiej sekwencji wejściowych.  
  
 ![Grafika przedstawiająca działania z wyjątkiem&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Pokazuje działanie z wyjątkiem.")  
  
### <a name="intersect"></a>INTERSECT  
 Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca części wspólnych dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a>Union  
 Poniższa ilustracja przedstawia operacji union na dwie sekwencje znaków. Zwracana sekwencja zawiera unikatowych elementów z obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca sumę dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Instrukcje: Łączenie i porównywanie kolekcji ciągów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
