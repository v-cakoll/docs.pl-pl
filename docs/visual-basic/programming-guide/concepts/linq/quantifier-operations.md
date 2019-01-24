---
title: Operacje kwantyfikatora (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0f732cdb51ed4e26039fc8c1d02b95ad32f901e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551933"
---
# <a name="quantifier-operations-visual-basic"></a>Operacje kwantyfikatora (Visual Basic)
Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.  
  
 Poniższa ilustracja przedstawia dwie operacje kwantyfikatora różnych na dwie sekwencje innego źródła. Pierwszą operacją pytaniem, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`. Pyta drugą operację, jeśli wszystkie elementy są znak "A", a wynik jest `true`.  
  
 ![Operacje kwantyfikatora LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Metody standardowego operatora zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Wszystkie|Określa, czy wszystkie elementy w sekwencji spełniają warunek.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Dowolne|Określa, czy dowolne elementy w sekwencji spełniają warunek.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Zawiera|Określa, czy sekwencja zawiera określony element.|Nie dotyczy.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
 Użyj tych przykładach `Aggregate` klauzuli w języku Visual Basic w ramach warunek filtrowania w zapytaniu programu LINQ.  
  
 W poniższym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.All%2A> metodę rozszerzenia, aby zwrócić ze zbioru osób, których zwierzęta są wszystkie starsze niż określona wieku.  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 W następnym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.Any%2A> metodę rozszerzenia, aby zwrócić z kolekcji, te osoby, które mają co najmniej jeden domowe, która jest starsza niż określona wieku.  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
