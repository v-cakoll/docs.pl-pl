---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f25ffb16fa5feb382bb42c737440317cfb777b1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666316"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> jest elementem synchronizacji, który odblokowuje wątków oczekujących, po przeprowadzeniu sygnalizowane, ile razy. <xref:System.Threading.CountdownEvent> jest przeznaczona dla scenariuszy, w których w przeciwnym razie trzeba byłoby użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> i ręcznie dekrementacyjne zmienną przed sygnalizacja zdarzenie. Na przykład w scenariuszu rozwidlenia/scalania, po prostu utworzeniem <xref:System.Threading.CountdownEvent> zawierający sygnału liczbę 5, a następnie rozpoczęcia pięć elementów roboczych w wątku puli i mieć każdego wywołania elementu roboczego <xref:System.Threading.CountdownEvent.Signal%2A> po zakończeniu. Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza sygnał liczba o 1. W głównym wątku, wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> blokuje, dopóki liczba sygnałów wynosi zero.  
  
> [!NOTE]
>  Dla kodu, który nie ma do interakcji z starszej wersji .NET Framework synchronizacji interfejsów API, należy wziąć pod uwagę przy użyciu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów lub <xref:System.Threading.Tasks.Parallel.Invoke%2A> metoda jeszcze łatwiejsze podejścia do wyrażania równoległości rozwidlenia sprzężenia.  
  
 <xref:System.Threading.CountdownEvent> ma te dodatkowe funkcje:  
  
- Przy użyciu tokenów anulowania można anulować operacji oczekiwania.  
  
- Po utworzeniu wystąpienia można zwiększyć jego Liczba sygnałów.  
  
- Wystąpienia mogą zostać ponownie użyte po <xref:System.Threading.CountdownEvent.Wait%2A> został zwrócony przez wywołanie metody <xref:System.Threading.CountdownEvent.Reset%2A> metody.  
  
- Udostępnianie wystąpień <xref:System.Threading.WaitHandle> integrację z innymi API synchronizacji .NET Framework takich jak <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Podstawowe użycia  
 Poniższy przykład pokazuje sposób użycia <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementów roboczych.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent w przypadku anulowania  
 Poniższy przykład pokazuje, jak można anulować operacji oczekiwania na <xref:System.Threading.CountdownEvent> przy użyciu tokenu anulowania. Podstawowy wzorzec następuje modelu ujednoliconego anulowania, która została wprowadzona w systemie [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Należy pamiętać, operacji oczekiwania nie powoduje anulowania wątków, które są sygnalizowanie go. Zazwyczaj anulowania jest stosowany do operacji logicznej i który może zawierać oczekiwania na zdarzenie, a także wszystkie elementy robocze, które synchronizuje czas oczekiwania. W tym przykładzie każdy element roboczy jest przekazywany kopię tego samego tokenu anulowania, aby go mogą odpowiadać na żądania anulowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
