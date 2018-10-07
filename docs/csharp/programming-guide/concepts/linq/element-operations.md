---
title: Operacje na elementach (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: dbae8c0b3d98fe9674fbbeb432c1e42763e81026
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836780"
---
# <a name="element-operations-c"></a>Operacje na elementach (C#)

Operacje na elementach Zwróć element jednej, określonej sekwencji.  
  
 Metody standardowego operatora zapytań, które wykonują operacje na elementach są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Zwraca element z określonym indeksem w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Zwraca element pod określonym indeksem w kolekcji lub wartość domyślną, jeśli indeks jest poza zakresem.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|pierwszy|Zwraca pierwszy element kolekcji lub pierwszego elementu, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Zwraca pierwszy element kolekcji lub pierwszego elementu, który spełnia warunek. Zwraca wartość domyślną, jeśli taki element nie istnieje.|Nie dotyczy.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|ostatni|Zwraca ostatni element kolekcji lub ostatniego elementu, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|Lastordefault —|Zwraca ostatni element kolekcji lub ostatniego elementu, który spełnia warunek. Zwraca wartość domyślną, jeśli taki element nie istnieje.|Nie dotyczy.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Zwraca tylko element kolekcji lub jedynym elementem, który spełnia warunek. Zgłasza <xref:System.InvalidOperationException> przypadku żaden element lub więcej niż jednego elementu do zwrócenia. |Nie dotyczy.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Zwraca tylko element kolekcji lub jedynym elementem, który spełnia warunek. Zwraca wartość domyślną, jeśli nie ma żadnego elementu do zwrócenia. Zgłasza <xref:System.InvalidOperationException> Jeśli istnieje więcej niż jednego elementu do zwrócenia. |Nie dotyczy.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>  
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
