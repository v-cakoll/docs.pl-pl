---
title: Zdarzenia ETW w bibliotece równoległych zadań i PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
ms.openlocfilehash: 61429babf7378b9d271ffd60a6228ae4bfe7a5e5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644246"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Zdarzenia ETW w bibliotece równoległych zadań i PLINQ

Zarówno biblioteka równoległa zadań, jak i PLINQ generują zdarzenia śledzenia zdarzeń dla systemu Windows (ETW), których można używać do profilowania i rozwiązywania problemów z aplikacjami przy użyciu narzędzi, takich jak analizator wydajności systemu Windows. Jednak w większości scenariuszy najlepszym sposobem profilu równoległego kodu aplikacji jest użycie [wizualizatora współbieżności](/visualstudio/profiling/concurrency-visualizer) w programie Visual Studio.

## <a name="task-parallel-library-etw-events"></a>Zdarzenia ETW biblioteki równoległej zadań

W strukturze EVENT_HEADER identyfikator GUID identyfikatora providerid <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> dla <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> zdarzeń generowanych przez program i jest:

`0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5`

### <a name="parallel-loop-begin"></a>Rozpoczęcie pętli równoległej

EVENT_DESCRIPTOR. Zadanie = 1

EVENT_DESCRIPTOR. Identyfikator = 1

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator narzędzia TaskScheduler, który rozpoczął pętlę.|
|Idea z zadaniami źródłowym|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które rozpoczęło pętlę.|
|Element ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazywania zagnieżdżania i par dla zdarzeń z semantyką rozwidleniem/sprzężeniem.|
|Operationtype|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ pętli:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|WłącznieOd|<xref:System.Int64?displayProperty=nameWithType>|Wartość początkowa licznika pętli|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Wartość końcowa licznika pętli|

### <a name="parallel-loop-end"></a>Końcowy pętla równoległa
 EVENT_DESCRIPTOR. Zadanie = 2

 EVENT_DESCRIPTOR. Identyfikator = 2

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator narzędzia TaskScheduler, który rozpoczął pętlę.|
|Idea z zadaniami źródłowym|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które rozpoczęło pętlę.|
|Element ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazywania zagnieżdżania i par dla zdarzeń z semantyką rozwidleniem/sprzężeniem.|
|sumaIteracje|<xref:System.Int64?displayProperty=nameWithType>|Całkowita liczba iteracji|

### <a name="parallel-invoke-begin"></a>Rozpoczęcie wywołania równoległego
 EVENT_DESCRIPTOR. Zadanie = 3

 EVENT_DESCRIPTOR. Identyfikator = 3

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator narzędzia TaskScheduler, który rozpoczął pętlę.|
|Idea z zadaniami źródłowym|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które rozpoczęło pętlę.|
|Element ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazywania zagnieżdżania i par dla zdarzeń z semantyką rozwidleniem/sprzężeniem.|
|sumaIteracje|<xref:System.Int64?displayProperty=nameWithType>|Całkowita liczba iteracji|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ pętli:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|Liczba akcji|<xref:System.Int32?displayProperty=nameWithType>|Liczba akcji, które będą wykonywane równolegle wywołać.|

### <a name="parallel-invoke-end"></a>Zakończenie wywołania równoległego
 EVENT_DESCRIPTOR. Zadanie = 4

 EVENT_DESCRIPTOR. Identyfikator = 4

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator narzędzia TaskScheduler, który rozpoczął pętlę.|
|Idea z zadaniami źródłowym|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które rozpoczęło pętlę.|
|Element ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazywania zagnieżdżania i par dla zdarzeń z semantyką rozwidleniem/sprzężeniem.|

## <a name="plinq-etw-events"></a>Wydarzenia PLINQ ETW
 The EVENT_HEADER. ProviderId GUID dla PLINQ jest:

`0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87`

### <a name="parallel-query-begin"></a>Rozpoczęcie kwerendy równoległej
 EVENT_DESCRIPTOR. Zadanie = 1

 EVENT_DESCRIPTOR. Identyfikator = 1

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator narzędzia TaskScheduler, który rozpoczął pętlę.|
|Idea z zadaniami źródłowym|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które rozpoczęło pętlę.|
|QueryID (IDA kwerendy)|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator kwerendy.|

### <a name="parallel-query-end"></a>Zakończenie kwerendy równoległej
 EVENT_DESCRIPTOR. Zadanie = 2

 EVENT_DESCRIPTOR. Identyfikator = 2

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator narzędzia TaskScheduler, który rozpoczął pętlę.|
|Idea z zadaniami źródłowym|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadania, które rozpoczęło pętlę.|
|QueryID (IDA kwerendy)|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator kwerendy.|

## <a name="see-also"></a>Zobacz też

- [Zdarzenia ETW w programie .NET Framework](etw-events.md)
- [Biblioteka zadań równoległych (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Równoległe LINQ (PLINQ)](../../standard/parallel-programming/introduction-to-plinq.md)
