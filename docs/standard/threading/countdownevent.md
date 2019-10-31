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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138110"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> to element pierwotny synchronizacji, który odblokowuje oczekujące wątki po zasygnalizowaniu określonej liczby razy. <xref:System.Threading.CountdownEvent> jest zaprojektowana dla scenariuszy, w których w przeciwnym razie należy użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> ręcznie zmniejszyć zmienną przed zasygnalizowaniem zdarzenia. Na przykład w scenariuszu rozwidlenie/łączenie można po prostu utworzyć <xref:System.Threading.CountdownEvent>, który ma liczbę sygnałów równą 5, a następnie rozpocząć pięć elementów roboczych w puli wątków i mieć każde wywołanie elementu pracy, <xref:System.Threading.CountdownEvent.Signal%2A> po jego zakończeniu. Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczbę sygnałów o 1. W wątku głównym wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> będzie blokowane, dopóki liczba sygnałów nie będzie równa zero.  
  
> [!NOTE]
> W przypadku kodu, który nie musi współdziałać ze starszymi interfejsami API synchronizacji .NET Framework, rozważ użycie obiektów <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub metody <xref:System.Threading.Tasks.Parallel.Invoke%2A> w celu uzyskania jeszcze łatwiejszego podejścia do wyznaczania równoległości przyłączania rozwidlenia.  
  
 <xref:System.Threading.CountdownEvent> ma następujące dodatkowe funkcje:  
  
- Operację oczekiwania można anulować przy użyciu tokenów anulowania.  
  
- Po utworzeniu wystąpienia można zwiększyć jego liczbę sygnałów.  
  
- Wystąpienia mogą być ponownie używane po zwróceniu <xref:System.Threading.CountdownEvent.Wait%2A>, wywołując metodę <xref:System.Threading.CountdownEvent.Reset%2A>.  
  
- Wystąpienia uwidaczniają <xref:System.Threading.WaitHandle> do integracji z innymi interfejsami API synchronizacji .NET Framework, takimi jak <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Podstawowe użycie  
 Poniższy przykład ilustruje sposób używania <xref:System.Threading.CountdownEvent> z <xref:System.Threading.ThreadPool> elementami roboczymi.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent z anulowaniem  
 Poniższy przykład pokazuje, jak anulować operację oczekiwania na <xref:System.Threading.CountdownEvent> przy użyciu tokenu anulowania. Wzorzec podstawowy jest zgodny z modelem dla ujednoliconego anulowania, który został wprowadzony w .NET Framework 4. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Należy pamiętać, że operacja oczekiwania nie anuluje wątków, które je sygnalizujący. Zazwyczaj anulowanie jest stosowane do operacji logicznej i może obejmować oczekiwanie na zdarzenie, a także wszystkie elementy robocze, które trwają synchronizacja. W tym przykładzie każdy element roboczy otrzymuje kopię tego samego tokenu anulowania, aby mógł on odpowiedzieć na żądanie anulowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
