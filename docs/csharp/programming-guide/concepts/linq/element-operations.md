---
title: Operacje elementów (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: e9ec41793afffe60a7184622f91b5fc023e0958f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345157"
---
# <a name="element-operations-c"></a>Operacje elementów (C#)

Operacje elementu zwracają pojedynczy, określony element z sekwencji.  
  
 Standardowe metody operatora kwerendy, które wykonują operacje elementu są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Elementat|Zwraca element w określonym indeksie w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementatorDefault|Zwraca element w określonym indeksie w kolekcji lub wartość domyślną, jeśli indeks jest poza zakresem.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|First|Zwraca pierwszy element kolekcji lub pierwszy element, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|Firstordefault|Zwraca pierwszy element kolekcji lub pierwszy element, który spełnia warunek. Zwraca wartość domyślną, jeśli nie istnieje żaden taki element.|Nie dotyczy.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Last|Zwraca ostatni element kolekcji lub ostatni element, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastorDefault (LastorDefault)|Zwraca ostatni element kolekcji lub ostatni element, który spełnia warunek. Zwraca wartość domyślną, jeśli nie istnieje żaden taki element.|Nie dotyczy.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Zwraca tylko element kolekcji lub tylko element, który spełnia warunek. <xref:System.InvalidOperationException> Zgłasza, jeśli nie ma żadnego elementu lub więcej niż jeden element do zwrócenia. |Nie dotyczy.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|Singleordefault|Zwraca tylko element kolekcji lub tylko element, który spełnia warunek. Zwraca wartość domyślną, jeśli nie ma żadnego elementu do zwrócenia. Zgłasza, <xref:System.InvalidOperationException> jeśli istnieje więcej niż jeden element do zwrócenia. |Nie dotyczy.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Jak wysyłać zapytania o największy plik lub pliki w drzewie katalogów (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
