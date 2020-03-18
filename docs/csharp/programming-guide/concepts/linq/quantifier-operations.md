---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635486"
---
# <a name="quantifier-operations-c"></a>Operacje kwantyfikatora (C#)
Operacje kwantyfikatora <xref:System.Boolean> zwraca wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.  
  
 Na poniższej ilustracji przedstawiono dwie różne operacje kwantyfikatora na dwóch różnych sekwencji źródłowych. Pierwsza operacja pyta, czy jeden lub więcej elementów to znak "A", a wynik jest `true`. Druga operacja pyta, czy wszystkie elementy są znakiem "A", a wynik jest `true`.  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardowe metody operatora kwerendy, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Wszystkie|Określa, czy wszystkie elementy w sekwencji spełniają warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Dowolne|Określa, czy wszystkie elementy w sekwencji spełniają warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contains|Określa, czy sekwencja zawiera określony element.|Nie dotyczy.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażenia kwerendy  
  
### <a name="all"></a>Wszystkie  
W poniższym `All` przykładzie użyto, aby sprawdzić, czy wszystkie ciągi mają określoną długość.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Dowolne  
W poniższym `Any` przykładzie użyto, aby sprawdzić, czy wszystkie ciągi są uruchamiane z "o".  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Contains  
W poniższym `Contains` przykładzie użyto do sprawdzenia tablicy mają określony element.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Jak wysyłać zapytania do zdań zawierających określony zestaw słów (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
