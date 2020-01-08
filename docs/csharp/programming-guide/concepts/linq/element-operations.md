---
title: Operacje elementu (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: e9ec41793afffe60a7184622f91b5fc023e0958f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345157"
---
# <a name="element-operations-c"></a>Operacje elementu (C#)

Operacje elementu zwracają pojedynczy, konkretny element z sekwencji.  
  
 W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje na elementach.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Zwraca element o określonym indeksie w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Zwraca element pod określonym indeksem w kolekcji lub wartość domyślną, jeśli indeks jest poza zakresem.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|First|Zwraca pierwszy element kolekcji lub pierwszy element, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Zwraca pierwszy element kolekcji lub pierwszy element, który spełnia warunek. Zwraca wartość domyślną, jeśli taki element nie istnieje.|Nie dotyczy.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Ostatnia|Zwraca ostatni element kolekcji lub ostatni element, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Zwraca ostatni element kolekcji lub ostatni element, który spełnia warunek. Zwraca wartość domyślną, jeśli taki element nie istnieje.|Nie dotyczy.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Zwraca jedyny element kolekcji lub jedynego elementu, który spełnia warunek. Zgłasza <xref:System.InvalidOperationException>, jeśli nie ma elementu lub więcej niż jeden element do zwrócenia. |Nie dotyczy.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Zwraca jedyny element kolekcji lub jedynego elementu, który spełnia warunek. Zwraca wartość domyślną, jeśli nie ma elementu do zwrócenia. Zgłasza <xref:System.InvalidOperationException>, jeśli istnieje więcej niż jeden element do zwrócenia. |Nie dotyczy.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [Jak wykonać zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
