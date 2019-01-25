---
title: Zdarzenia ETW w bibliotece równoległych zadań i PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85ca55e976a010a4875d260b3da30f5bc3cf2ffb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740154"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Zdarzenia ETW w bibliotece równoległych zadań i PLINQ

Biblioteka równoległych zadań i PLINQ generowanie zdarzeń zdarzeń śledzenia dla Windows (ETW), które można użyć na potrzeby profilowania i rozwiązywanie problemów z aplikacjami za pomocą narzędzi, takich jak Windows Analizator wydajności. Jednak w większości przypadków najlepszym sposobem na kod aplikacji równoległych profilu jest użycie [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer) w programie Visual Studio.

## <a name="task-parallel-library-etw-events"></a>Zdarzenia ETW w bibliotece równoległych zadań

W strukturze EVENT_HEADER identyfikator GUID identyfikator zdarzenia generowane przez <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> jest:

```
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5
```

### <a name="parallel-loop-begin"></a>Rozpocznij pętli równoległej

EVENT_DESCRIPTOR. Zadanie = 1

EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator harmonogramu zadań systemu, który uruchomił pętli.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadanie, które uruchomiło pętli.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżanie i pary zdarzeń z semantyką rozwidlenia/scalania.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ Pętla:<br /><br /> 1 = równoległego<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Wartością początkową licznika pętli|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Końcowa wartość licznika pętli|

### <a name="parallel-loop-end"></a>Zakończenia pętli równoległej
 EVENT_DESCRIPTOR. Zadanie = 2

 EVENT_DESCRIPTOR. Identyfikator = 2

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator harmonogramu zadań systemu, który uruchomił pętli.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadanie, które uruchomiło pętli.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżanie i pary zdarzeń z semantyką rozwidlenia/scalania.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Całkowita liczba iteracji|

### <a name="parallel-invoke-begin"></a>Wywoływanie równolegle Begin
 EVENT_DESCRIPTOR.Task = 3

 EVENT_DESCRIPTOR.Id = 3

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator harmonogramu zadań systemu, który uruchomił pętli.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadanie, które uruchomiło pętli.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżanie i pary zdarzeń z semantyką rozwidlenia/scalania.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Całkowita liczba iteracji|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Wskazuje typ Pętla:<br /><br /> 1 = równoległego<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Liczba akcji, które będą wykonywane w równoległych invoke.|

### <a name="parallel-invoke-end"></a>Równoległe wywołania zakończenia
 EVENT_DESCRIPTOR.Task = 4

 EVENT_DESCRIPTOR.Id = 4

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator harmonogramu zadań systemu, który uruchomił pętli.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadanie, które uruchomiło pętli.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Unikatowy identyfikator używany do wskazania zagnieżdżanie i pary zdarzeń z semantyką rozwidlenia/scalania.|

## <a name="plinq-etw-events"></a>Zdarzenia ETW w PLINQ
 EVENT_HEADER. Identyfikator GUID dla PLINQ jest:

```
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87
```

### <a name="parallel-query-begin"></a>Początek zapytania równoległe
 EVENT_DESCRIPTOR. Zadanie = 1

 EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator harmonogramu zadań systemu, który uruchomił pętli.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadanie, które uruchomiło pętli.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator unikatowy kwerendy.|

### <a name="parallel-query-end"></a>Koniec zapytania równoległe
 EVENT_DESCRIPTOR. Zadanie = 2

 EVENT_DESCRIPTOR. Identyfikator = 2

#### <a name="user-data"></a>Dane użytkownika

|**Nazwa**|**Typ**|**Opis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator harmonogramu zadań systemu, który uruchomił pętli.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator zadanie, które uruchomiło pętli.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Identyfikator unikatowy kwerendy.|

## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW w programie .NET Framework](../../../docs/framework/performance/etw-events.md)
- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
