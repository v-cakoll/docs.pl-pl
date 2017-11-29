---
title: CountdownEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f953f6477abf1f4e0d6aaf79e67005172ff1144
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>jest prymitywu synchronizacji, który odblokowuje wątków oczekiwania, po przeprowadzeniu sygnalizowane wiele razy. <xref:System.Threading.CountdownEvent>jest przeznaczony do scenariuszy, w których mogłyby w przeciwnym razie należy użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> i ręcznie dekrementacji zmiennej przed sygnalizowania zdarzenia. Na przykład w przypadku rozwidlenia/sprzężenia, po prostu utworzeniem <xref:System.Threading.CountdownEvent> mający sygnału liczbę 5, a następnie start pięć elementów roboczych w wątku puli i mieć każdego wywołania elementu roboczego <xref:System.Threading.CountdownEvent.Signal%2A> po zakończeniu wykonywania. Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczba sygnał o 1. W głównym wątku wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> zablokuje dopóki liczba sygnałów wynosi zero.  
  
> [!NOTE]
>  Kod, który nie ma na interakcję z starszej wersji .NET Framework synchronizacji interfejsów API, należy rozważyć użycie <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów lub <xref:System.Threading.Tasks.Parallel.Invoke%2A> metody łatwiejsze podejścia do wyrażania równoległości rozwidlenia sprzężenia.  
  
 <xref:System.Threading.CountdownEvent>ma następujące dodatkowe funkcje:  
  
-   Za pomocą tokenów anulowania można anulować operacji oczekiwania.  
  
-   Po utworzeniu wystąpienia można odpowiednio licznika sygnału.  
  
-   Można ponownie użyć wystąpienia po <xref:System.Threading.CountdownEvent.Wait%2A> został zwrócony przez wywołanie metody <xref:System.Threading.CountdownEvent.Reset%2A> metody.  
  
-   Udostępnianie wystąpień <xref:System.Threading.WaitHandle> do integracji z innymi synchronizacji .NET Framework interfejsów API takich jak <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Podstawowe sposoby użycia  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementów roboczych.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent z anulowania  
 Poniższy przykład przedstawia sposób anulowania operacji oczekiwania na <xref:System.Threading.CountdownEvent> przy użyciu token anulowania. Podstawowy wzorzec jest zgodna ze modelem ujednoliconego anulowania, która została wprowadzona w systemie [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Uwaga operacji oczekiwania nie spowoduje anulowania wątków, które są sygnalizowania go. Zazwyczaj anulowania jest stosowany do operacji logicznych i który może zawierać oczekiwania na zdarzenie, a także wszystkie elementy robocze, które synchronizuje czas oczekiwania. W tym przykładzie każdy element roboczy jest przekazywany kopię tego samego token anulowania, dzięki czemu mogą odpowiadać na żądania anulowania.  
  
## <a name="see-also"></a>Zobacz też  
 [EventWaitHandle, autoresetevent —, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
