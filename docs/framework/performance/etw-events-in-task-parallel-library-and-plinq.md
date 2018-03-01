---
title: "Zdarzenia ETW w bibliotece równoległych zadań i PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a84fdb104296cf15b5f0d2d04f4ddd7ea1419643
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Zdarzenia ETW w bibliotece równoległych zadań i PLINQ
Zarówno bibliotece równoległych zadań i PLINQ generowanie zdarzeń śledzenia zdarzeń systemu Windows (ETW) zdarzenia, które służy do profilu i rozwiązywania problemów z aplikacjami za pomocą narzędzi, takich jak Analizator wydajności systemu Windows. Jednak w większości przypadków najlepszym sposobem na kod aplikacji równoległych profilem jest użycie [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) w [!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)].  
  
## <a name="task-parallel-library-etw-events"></a>Zdarzenia ETW w bibliotece równoległych zadań  
 W strukturze EVENT_HEADER zdarzenia generowane przez identyfikator GUID ProviderId <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> jest:  
  
```  
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5  
```  
  
### <a name="parallel-loop-begin"></a>Rozpocznij równoległej pętli  
 EVENT_DESCRIPTOR. Zadanie = 1  
  
 EVENT_DESCRIPTOR. Identyfikator = 1  
  
#### <a name="user-data"></a>Dane użytkownika  
  
|**Nazwa**|**Typ**|**Opis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętli.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomione pętli.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator, który służy do wskazania pary zdarzeń o semantyki rozwidlenia/sprzężenia i zagnieżdżenia.|  
|Typ operacji|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ Pętla:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = działania ParallelForEach|  
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Początkowej wartości licznika pętli|  
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Wartości końcowej licznika pętli|  
  
### <a name="parallel-loop-end"></a>Końcowy równoległej pętli  
 EVENT_DESCRIPTOR. Zadanie = 2  
  
 EVENT_DESCRIPTOR. Identyfikator = 2  
  
#### <a name="user-data"></a>Dane użytkownika  
  
|**Nazwa**|**Typ**|**Opis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętli.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomione pętli.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator, który służy do wskazania pary zdarzeń o semantyki rozwidlenia/sprzężenia i zagnieżdżenia.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Całkowita liczba iteracji|  
  
### <a name="parallel-invoke-begin"></a>Równoległe wywołania Begin  
 EVENT_DESCRIPTOR. Zadanie = 3  
  
 EVENT_DESCRIPTOR. Identyfikator = 3  
  
#### <a name="user-data"></a>Dane użytkownika  
  
|**Nazwa**|**Typ**|**Opis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętli.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomione pętli.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator, który służy do wskazania pary zdarzeń o semantyki rozwidlenia/sprzężenia i zagnieżdżenia.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Całkowita liczba iteracji|  
|Typ operacji|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ Pętla:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = działania ParallelForEach|  
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Liczba działań, które będą wykonywane w równoległych invoke.|  
  
### <a name="parallel-invoke-end"></a>Równoległe wywołania zakończenia  
 EVENT_DESCRIPTOR. Zadanie = 4  
  
 EVENT_DESCRIPTOR. Identyfikator = 4  
  
#### <a name="user-data"></a>Dane użytkownika  
  
|**Nazwa**|**Typ**|**Opis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętli.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomione pętli.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator, który służy do wskazania pary zdarzeń o semantyki rozwidlenia/sprzężenia i zagnieżdżenia.|  
  
## <a name="plinq-etw-events"></a>Zdarzenia PLINQ ETW  
 EVENT_HEADER. Identyfikator GUID ProviderId PLINQ jest:  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### <a name="parallel-query-begin"></a>Rozpocznij zapytania równoległe  
 EVENT_DESCRIPTOR. Zadanie = 1  
  
 EVENT_DESCRIPTOR. Identyfikator = 1  
  
#### <a name="user-data"></a>Dane użytkownika  
  
|**Nazwa**|**Typ**|**Opis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętli.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomione pętli.|  
|Identyfikatora kwerendy|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator unikatowy zapytania.|  
  
### <a name="parallel-query-end"></a>Zapytania równoległe zakończenia  
 EVENT_DESCRIPTOR. Zadanie = 2  
  
 EVENT_DESCRIPTOR. Identyfikator = 2  
  
#### <a name="user-data"></a>Dane użytkownika  
  
|**Nazwa**|**Typ**|**Opis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętli.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomione pętli.|  
|Identyfikatora kwerendy|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator unikatowy zapytania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia ETW w programie .NET Framework](../../../docs/framework/performance/etw-events.md)  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
