---
title: Partycjonowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: b857c8c6e6b56a7263e6725a747e98ccfe4ff4fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832466"
---
# <a name="partitioning-data-c"></a>Partycjonowanie danych (C#)
Partycjonowanie w składniku LINQ odnosi się do funkcjonowania dzielenie sekwencji wejściowych na dwie sekcje bez rozmieszczanie elementów, a następnie powrotu w sekcji.  
  
 Poniższa ilustracja przedstawia wyniki trzech różnych partycjonowania operacji na sekwencję znaków. Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji. Drugą operację pomija pierwszych trzech elementów i zwraca wszystkie pozostałe elementy. Operacja trzeci pomija pierwszych dwóch elementów w sekwencji i zwraca następne trzy elementy.  
  
 ![Ilustracja przedstawiająca trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Metody standardowego operatora zapytań, partycji sekwencji, które są wymienione w poniższej sekcji.  
  
## <a name="operators"></a>Operatory  
  
|Nazwa operatora|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Pomija elementy do określonej pozycji w sekwencji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Pomija elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.|Nie dotyczy.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Pobiera elementy do określonej pozycji w sekwencji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.|Nie dotyczy.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
