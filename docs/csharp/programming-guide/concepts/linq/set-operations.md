---
title: Ustawianie operacji (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 44a145a625b5e2e16d2469b20f8cfda1858560a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167936"
---
# <a name="set-operations-c"></a>Ustawianie operacji (C#)
Set operations in LINQ odnoszą się do operacji kwerendy, które produkują zestaw wyników, który jest oparty na obecności lub braku równoważnych elementów w ramach tych samych lub oddzielnych kolekcji (lub zestawów).  
  
 Standardowe metody operatora kwerendy, które wykonują operacje zestawu są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Usuwa zduplikowane wartości z kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Z wyjątkiem|Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie są wyświetlane w drugiej kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Przecinają się|Zwraca zestaw przecięcia, co oznacza elementy, które pojawiają się w każdej z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Unia|Zwraca zestaw unii, co oznacza unikatowe elementy, które pojawiają się w jednej z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porównanie operacji zestawu  
  
### <a name="distinct"></a>Distinct  
 Poniższy przykład przedstawia zachowanie metody <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> na sekwencji znaków. Zwrócona sekwencja zawiera unikatowe elementy z sekwencji wejściowej.  
  
 ![Grafika przedstawiająca zachowanie distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a>Z wyjątkiem  
 Poniższy przykład przedstawia zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Zwrócona sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowej, które nie znajdują się w drugiej sekwencji wejściowej.  
  
 ![Grafika przedstawiająca działanie z wyjątkiem&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Pokazuje zachowanie except.")  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a>Przecinają się  
 Poniższy przykład przedstawia zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Zwrócona sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca przecięcie dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a>Unia  
 Poniższy przykład przedstawia operację unii na dwóch sekwencjach znaków. Zwrócona sekwencja zawiera unikatowe elementy z obu sekwencji wejściowych.  
  
 ![Grafika przedstawiająca połączenie dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Jak łączyć i porównywać kolekcje ciągów (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)
- [Jak znaleźć różnicę między dwiema listami (LINQ) (C#)](./how-to-find-the-set-difference-between-two-lists-linq.md)
