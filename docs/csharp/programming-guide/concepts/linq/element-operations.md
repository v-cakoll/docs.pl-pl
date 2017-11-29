---
title: Operacje na elementach (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 55081e66419624c2c4930a254d3d464007477766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="element-operations-c"></a>Operacje na elementach (C#)
Operacje na elementach zwrócić element jednej, określonej sekwencji.  
  
 Metody operator standardowe zapytań, które wykonują operacje na elementach są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Zwraca element pod określonym indeksem w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Zwraca element pod określonym indeksem w kolekcji lub wartość domyślną, jeśli indeks jest poza zakresem.|Nie dotyczy.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|pierwszy|Zwraca pierwszy element kolekcji lub pierwszym elementem, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Zwraca pierwszy element kolekcji lub pierwszym elementem, który spełnia warunek. Zwraca wartość domyślną, jeśli nie zawiera żadnego takiego elementu.|Nie dotyczy.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|ostatni|Zwraca ostatni element kolekcji lub ostatniego elementu, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Zwraca ostatni element kolekcji lub ostatniego elementu, który spełnia warunek. Zwraca wartość domyślną, jeśli nie zawiera żadnego takiego elementu.|Nie dotyczy.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Zwraca jedynym elementem kolekcji lub jedynym elementem, który spełnia warunek.|Nie dotyczy.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Zwraca jedynym elementem kolekcji lub jedynym elementem, który spełnia warunek. Zwraca wartość domyślną, jeśli nie zawiera żadnego takiego elementu lub kolekcja nie zawiera dokładnie jeden element.|Nie dotyczy.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
