---
title: Zdarzenia ETW w bibliotece równoległych zadań i PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 611ad0a6f4ec8b8c63010938372b733a0ac66052
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955766"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Zdarzenia ETW w bibliotece równoległych zadań i PLINQ

Biblioteka zadań równoległych i PLINQ generują zdarzenia śledzenia zdarzeń dla systemu Windows (ETW), których można użyć do profilowania i rozwiązywania problemów z aplikacjami przy użyciu narzędzi, takich jak Windows Performance Analyzer. Jednak w większości scenariuszy najlepszym sposobem profilowania kodu aplikacji równoległej jest użycie wizualizatora współbieżności w [](/visualstudio/profiling/concurrency-visualizer) programie Visual Studio.

## <a name="task-parallel-library-etw-events"></a>Zdarzenia ETW biblioteki równoległej zadania

W strukturze EVENT_HEADER identyfikator GUID identyfikatorem dla zdarzeń generowanych przez <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> :

```
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5
```

### <a name="parallel-loop-begin"></a>Rozpoczęcie pętli równoległej

EVENT_DESCRIPTOR. Zadanie = 1

EVENT_DESCRIPTOR. Identyfikator = 1

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętlę.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomiło pętlę.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżenia i par dla zdarzeń z semantyką rozwidlenia/sprzężenia.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ pętli:<br /><br /> 1 = równoległego wywoływania metody<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Wartość początkowa licznika pętli|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Wartość końcowa licznika pętli|

### <a name="parallel-loop-end"></a>Zakończenie pętli równoległej
 EVENT_DESCRIPTOR. Zadanie = 2

 EVENT_DESCRIPTOR. Identyfikator = 2

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętlę.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomiło pętlę.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżenia i par dla zdarzeń z semantyką rozwidlenia/sprzężenia.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Łączna liczba iteracji|

### <a name="parallel-invoke-begin"></a>Początek wywołania równoległego
 EVENT_DESCRIPTOR. Zadanie = 3

 EVENT_DESCRIPTOR. Identyfikator = 3

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętlę.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomiło pętlę.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżenia i par dla zdarzeń z semantyką rozwidlenia/sprzężenia.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Łączna liczba iteracji|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ pętli:<br /><br /> 1 = równoległego wywoływania metody<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Liczba akcji, które zostaną wykonane w wywołaniu równoległym.|

### <a name="parallel-invoke-end"></a>Zakończenie wywołania równoległego
 EVENT_DESCRIPTOR. Zadanie = 4

 EVENT_DESCRIPTOR. Identyfikator = 4

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętlę.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomiło pętlę.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżenia i par dla zdarzeń z semantyką rozwidlenia/sprzężenia.|

## <a name="plinq-etw-events"></a>Zdarzenia ETW PLINQ
 EVENT_HEADER. Identyfikator GUID identyfikatorem dla PLINQ to:

```
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87
```

### <a name="parallel-query-begin"></a>Rozpoczęcie zapytania równoległego
 EVENT_DESCRIPTOR. Zadanie = 1

 EVENT_DESCRIPTOR. Identyfikator = 1

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętlę.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomiło pętlę.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator zapytania.|

### <a name="parallel-query-end"></a>Równoległe zakończenie zapytania
 EVENT_DESCRIPTOR. Zadanie = 2

 EVENT_DESCRIPTOR. Identyfikator = 2

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator TaskScheduler, który uruchomił pętlę.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które uruchomiło pętlę.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator zapytania.|

## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW w programie .NET Framework](../../../docs/framework/performance/etw-events.md)
- [Biblioteka zadań równoległych (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Równoległe LINQ (PLINQ)](../../standard/parallel-programming/parallel-linq-plinq.md)
