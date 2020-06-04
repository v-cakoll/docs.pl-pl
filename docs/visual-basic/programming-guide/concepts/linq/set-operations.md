---
title: Operacje na zestawie
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406823"
---
# <a name="set-operations-visual-basic"></a>Operacje Set (Visual Basic)

Operacje Set w LINQ odnoszą się do operacji zapytania, które tworzą zestaw wyników, który jest oparty na obecności lub braku równoważnych elementów w obrębie tych samych lub oddzielnych kolekcji (lub zestawów).

W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje na zestawach.

## <a name="methods"></a>Metody

|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|Usuwa zduplikowane wartości z kolekcji.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|Z wyjątkiem|Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie znajdują się w drugiej kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|Wspólnej|Zwraca część wspólną, która oznacza elementy, które pojawiają się w każdej z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|Unia|Zwraca zestaw zbiorów, co oznacza unikatowe elementy, które pojawiają się w jednej z dwóch kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>Porównanie operacji ustawiania

### <a name="distinct"></a>Distinct

Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody dla sekwencji znaków. Zwracana sekwencja zawiera unikatowe elementy z sekwencji wejściowej.

![Ilustracja przedstawiająca zachowanie odrębnych&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>Z wyjątkiem

Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> . Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowej, które nie znajdują się w drugiej sekwencji wejściowej.

![Ilustracja przedstawiająca akcję z wyjątkiem&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Pokazuje zachowanie z wyjątkiem.")

### <a name="intersect"></a>Wspólnej

Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> . Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.

![Ilustracja przedstawiająca przecięcie dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>Unia

Poniższa ilustracja przedstawia operację Union dla dwóch sekwencji znaków. Zwracana sekwencja zawiera unikatowe elementy z obu sekwencji wejściowych.

![Ilustracja przedstawiająca Unię dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania

W poniższym przykładzie zastosowano `Distinct` klauzulę w zapytaniu LINQ do zwrócenia unikatowych liczb z listy liczb całkowitych.

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Distinct, klauzula](../../../language-reference/queries/distinct-clause.md)
- [Instrukcje: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)
- [Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)
