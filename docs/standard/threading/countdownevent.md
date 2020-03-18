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
ms.openlocfilehash: 628d6a96606117d447c61d01595d13dd4a957ce4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138110"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>jest prymitywem synchronizacji, który odblokowuje jego wątki oczekiwania po tym, jak został zasygnalizowany określoną liczbę razy. <xref:System.Threading.CountdownEvent>jest przeznaczony dla scenariuszy, w których w <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim> przeciwnym razie trzeba by użyć lub ręcznie zmniejszać zmienną przed zasygnalizowaniem zdarzenia. Na przykład w scenariuszu rozwidlenie/sprzężenie można po prostu utworzyć, <xref:System.Threading.CountdownEvent> który ma liczbę sygnałów 5, a <xref:System.Threading.CountdownEvent.Signal%2A> następnie uruchomić pięć elementów roboczych w puli wątków i mieć każde wywołanie elementu pracy po zakończeniu. Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczbę sygnałów o 1. W wątku głównym wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> zostanie zablokowane, dopóki liczba sygnałów nie osiągnie zera.  
  
> [!NOTE]
> Dla kodu, który nie musi współdziałać ze starszymi <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> interfejsami <xref:System.Threading.Tasks.Parallel.Invoke%2A> API synchronizacji .NET Framework, należy rozważyć użycie obiektów lub metody dla jeszcze łatwiejszego podejścia do wyrażania równoległości sprzężenia rozwidliwego.  
  
 <xref:System.Threading.CountdownEvent>posiada następujące dodatkowe funkcje:  
  
- Operację oczekiwania można anulować przy użyciu tokenów anulowania.  
  
- Jego liczba sygnałów może być zwiększana po utworzeniu wystąpienia.  
  
- Wystąpienia mogą być ponownie <xref:System.Threading.CountdownEvent.Wait%2A> używane po powrocie przez wywołanie <xref:System.Threading.CountdownEvent.Reset%2A> metody.  
  
- Wystąpienia uwidaczniają <xref:System.Threading.WaitHandle> do integracji z innymi <xref:System.Threading.WaitHandle.WaitAll%2A>interfejsami API synchronizacji programu .NET Framework, takimi jak .  
  
## <a name="basic-usage"></a>Podstawowe użycie  
 W poniższym przykładzie pokazano, jak używać <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementami roboczymi.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>Odliczanie zdarzenia z anulowaniem  
 W poniższym przykładzie pokazano, <xref:System.Threading.CountdownEvent> jak anulować operację oczekiwania przy użyciu tokenu anulowania. Podstawowy wzorzec następuje model ujednoliconego anulowania, który jest wprowadzany w .NET Framework 4. Aby uzyskać więcej informacji, zobacz [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Należy zauważyć, że operacja oczekiwania nie anuluje wątków, które ją sygnalizują. Zazwyczaj anulowanie jest stosowane do operacji logicznej i które mogą obejmować oczekiwanie na zdarzenie, a także wszystkie elementy robocze, które trwa synchronizacja oczekiwania. W tym przykładzie każdy element pracy jest przekazywana kopia tego samego tokenu anulowania, dzięki czemu można odpowiedzieć na żądanie anulowania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
