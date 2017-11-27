---
title: Operacje agregacji (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3bb029d2b7f9115d1c68db2844127329d34fe2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="aggregation-operations-c"></a>Operacje agregacji (C#)
Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości. Przykładem operacji agregacji oblicza średnią temperaturę codzienne z miesięcznej wartości dziennych temperatury.  
  
 Na poniższej ilustracji przedstawiono wyniki dwóch operacji różnych agregacji w sekwencji liczb. Pierwszą operacją sumuje liczby. Druga operacja zwraca maksymalną wartość w sekwencji.  
  
 ![Operacje agregacji LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 Metody operator standardowe zapytań, które wykonują operacje agregacji są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Agregowanie|Wykonuje operację agregacji niestandardowej na wartościach w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Średnia|Oblicza średnią wartość kolekcję wartości.|Nie dotyczy.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Liczba|Liczba elementów w kolekcji, opcjonalnie tylko te elementy, które spełniają funkcja predykatu.|Nie dotyczy.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Liczba elementów w kolekcji jest duży, opcjonalnie tylko te elementy, które spełniają funkcja predykatu.|Nie dotyczy.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maksymalna|Określa maksymalną wartość w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min|Określa minimalną wartość w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Suma|Oblicza sumę wartości w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Porady: obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 [Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
