---
title: Operacje agregacji (C#)
description: Dowiedz się więcej na temat metod wykonywania operacji agregacji. Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości.
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: 3d5a52249520478571db2fcfd7aa5d10fb013565
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104302"
---
# <a name="aggregation-operations-c"></a>Operacje agregacji (C#)
Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości. Przykład operacji agregacji oblicza średnią dzienną temperaturę od miesięcznej wartości dziennej temperatury.  
  
 Na poniższej ilustracji przedstawiono wyniki dwóch różnych operacji agregacji w sekwencji liczb. Pierwsza operacja sumuje liczby. Druga operacja zwraca maksymalną wartość w sekwencji.  
  
 ![Ilustracja przedstawiająca operacje agregacji LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje agregacji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Agregacja|Wykonuje niestandardową operację agregacji na wartościach kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Średnia|Oblicza średnią wartość kolekcji wartości.|Nie dotyczy.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Liczba|Zlicza elementy w kolekcji, opcjonalnie tylko te elementy, które spełniają funkcję predykatu.|Nie dotyczy.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Zlicza elementy w dużej kolekcji, opcjonalnie tylko te elementy, które spełniają funkcję predykatu.|Nie dotyczy.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks.|Określa maksymalną wartość w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min.|Określa minimalną wartość w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Suma|Oblicza sumę wartości w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (C#)](./standard-query-operators-overview.md)
- [Jak obliczyć wartości kolumn w pliku tekstowym CSV (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Jak wykonać zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Jak wykonać zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
