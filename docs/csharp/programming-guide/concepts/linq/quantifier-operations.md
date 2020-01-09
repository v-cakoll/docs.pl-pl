---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635486"
---
# <a name="quantifier-operations-c"></a>Operacje kwantyfikatora (C#)
Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość wskazującą, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.  
  
 Na poniższej ilustracji przedstawiono dwa różne operacje kwantyfikatora dla dwóch różnych sekwencji źródłowych. Pierwsza operacja pyta, czy co najmniej jeden element jest znakiem "A", a wynik jest `true`. Druga operacja pyta, czy wszystkie elementy są znakiem "A", a wynik jest `true`.  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardowe metody operatorów zapytań, które wykonują operacje kwantyfikatora, są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Wszystkie|Określa, czy wszystkie elementy w sekwencji spełniają warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Dowolne|Określa, czy dowolne elementy w sekwencji spełniają warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Zawiera|Określa, czy sekwencja zawiera określony element.|Nie dotyczy.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="all"></a>Wszystkie  
Poniższy przykład używa `All`, aby sprawdzić, czy wszystkie ciągi mają określoną długość.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Dowolne  
Poniższy przykład używa `Any`, aby sprawdzić, czy wszystkie ciągi zaczynają się od "o".  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Zawiera  
Poniższy przykład używa `Contains`, aby sprawdzić, czy tablica zawiera określony element.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Jak wykonać zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
