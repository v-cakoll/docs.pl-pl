---
title: Operacje kwantyfikatora
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: f5b98ec09405ca4b8c715dc7da342e66a5d434d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346581"
---
# <a name="quantifier-operations-visual-basic"></a>Operacje kwantyfikatora (Visual Basic)
Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość wskazującą, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.  
  
 Na poniższej ilustracji przedstawiono dwa różne operacje kwantyfikatora dla dwóch różnych sekwencji źródłowych. Pierwsza operacja pyta, czy co najmniej jeden element jest znakiem "A", a wynik jest `true`. Druga operacja pyta, czy wszystkie elementy są znakiem "A", a wynik jest `true`.  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardowe metody operatorów zapytań, które wykonują operacje kwantyfikatora, są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Wszyscy|Określa, czy wszystkie elementy w sekwencji spełniają warunek.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Dowolne|Określa, czy dowolne elementy w sekwencji spełniają warunek.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|zawiera|Określa, czy sekwencja zawiera określony element.|Nie dotyczy.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
 W poniższych przykładach użyto klauzuli `Aggregate` w Visual Basic jako część warunku filtrowania w zapytaniu LINQ.  
  
 W poniższym przykładzie zastosowano klauzulę `Aggregate` i metodę rozszerzenia <xref:System.Linq.Enumerable.All%2A>, aby zwrócić z kolekcji te osoby, których zwierzęta domowe są starsze niż określony wiek.  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 W następnym przykładzie zastosowano klauzulę `Aggregate` i metodę rozszerzenia <xref:System.Linq.Enumerable.Any%2A>, aby zwrócić z kolekcji osoby, które mają co najmniej jedną PET, która jest starsza od określonego wieku.  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Aggregate, klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Instrukcje: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
