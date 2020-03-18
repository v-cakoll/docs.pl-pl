---
title: Partycjonowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591591"
---
# <a name="partitioning-data-c"></a>Partycjonowanie danych (C#)
Partycjonowanie w LINQ odnosi się do operacji dzielenia sekwencji wejściowej na dwie sekcje, bez zmiany rozmieszczenia elementów, a następnie zwracanie jednej z sekcji.  
  
 Na poniższej ilustracji przedstawiono wyniki trzech różnych operacji partycjonowania sekwencji znaków. Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji. Druga operacja pomija pierwsze trzy elementy i zwraca pozostałe elementy. Trzecia operacja pomija pierwsze dwa elementy w sekwencji i zwraca następne trzy elementy.  
  
 ![Ilustracja, która pokazuje trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Standardowe metody operatora kwerendy, które sekwencje partycji są wymienione w poniższej sekcji.  
  
## <a name="operators"></a>Operatory  
  
|Nazwa operatora|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Pomija elementy do określonej pozycji w sekwencji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|Skipwhile|Pomija elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.|Nie dotyczy.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Pobiera elementy do określonej pozycji w sekwencji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|Takewhile|Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.|Nie dotyczy.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
