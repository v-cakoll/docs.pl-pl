---
title: Operacje Set (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: cea0c0ba4dd6c7f874f69e3ec4a179248397b67d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591120"
---
# <a name="set-operations-c"></a>Operacje Set (C#)
Operacje Set w LINQ odnoszą się do operacji zapytania, które tworzą zestaw wyników, który jest oparty na obecności lub braku równoważnych elementów w obrębie tych samych lub oddzielnych kolekcji (lub zestawów).  
  
 W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje na zestawach.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Usuwa zduplikowane wartości z kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Ale|Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie znajdują się w drugiej kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Wspólnej|Zwraca część wspólną, która oznacza elementy, które pojawiają się w każdej z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Union|Zwraca zestaw zbiorów, co oznacza unikatowe elementy, które pojawiają się w jednej z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porównanie operacji ustawiania  
  
### <a name="distinct"></a>Distinct  
 Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody dla sekwencji znaków. Zwracana sekwencja zawiera unikatowe elementy z sekwencji wejściowej.  
  
 ![Ilustracja przedstawiająca zachowanie różnych&#40;&#41;elementów.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a>Ale  
 Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowej, które nie znajdują się w drugiej sekwencji wejściowej.  
  
 ![Ilustracja przedstawiająca akcję z wyjątkiem&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Pokazuje zachowanie z wyjątkiem.")  
  
### <a name="intersect"></a>Wspólnej  
 Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.  
  
 ![Ilustracja przedstawiająca przecięcie dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a>Union  
 Poniższa ilustracja przedstawia operację Union dla dwóch sekwencji znaków. Zwracana sekwencja zawiera unikatowe elementy z obu sekwencji wejściowych.  
  
 ![Ilustracja przedstawiająca Unię dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [Instrukcje: Łączenie i porównywanie kolekcji ciągów (LINQ)C#()](./how-to-combine-and-compare-string-collections-linq.md)
- [Instrukcje: Znajdź różnicę między dwoma listami (LINQ) (C#)](./how-to-find-the-set-difference-between-two-lists-linq.md)
