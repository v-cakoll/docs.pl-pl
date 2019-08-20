---
title: Partycjonowanie danychC#()
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591591"
---
# <a name="partitioning-data-c"></a>Partycjonowanie danychC#()
Partycjonowanie w LINQ odwołuje się do operacji dzielenia sekwencji wejściowej na dwie sekcje, bez konieczności ponownej rozmieszczania elementów, a następnie zwrócenia jednej z sekcji.  
  
 Na poniższej ilustracji przedstawiono wyniki trzech różnych operacji partycjonowania na sekwencji znaków. Pierwsza operacja zwraca trzy pierwsze elementy w sekwencji. Druga operacja pomija pierwsze trzy elementy i zwraca pozostałe elementy. Trzecia operacja pomija pierwsze dwa elementy w sekwencji i zwraca następne trzy elementy.  
  
 ![Ilustracja przedstawiająca trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Standardowe metody operatorów zapytań, które są sekwencje partycji, są wymienione w poniższej sekcji.  
  
## <a name="operators"></a>Operatory  
  
|Nazwa operatora|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Pomija elementy do określonej pozycji w sekwencji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Pomija elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.|Nie dotyczy.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Pobiera elementy do określonej pozycji w sekwencji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile —|Pobiera elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.|Nie dotyczy.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
