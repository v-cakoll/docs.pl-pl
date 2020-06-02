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
ms.openlocfilehash: 8ed1414ad377015400d9e126d924bf426fbc753d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277859"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>jest pierwotną synchronizacją, która odblokowuje oczekujące wątki po zasygnalizowaniu określonej liczby razy. <xref:System.Threading.CountdownEvent>jest przeznaczony do scenariuszy, w których w przeciwnym razie trzeba będzie użyć <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim> ręcznie zmniejszyć zmienną przed zasygnalizowaniem zdarzenia. Na przykład w scenariuszu rozwidlenie/łączenie można po prostu utworzyć element <xref:System.Threading.CountdownEvent> , który ma liczbę sygnałów równą 5, a następnie rozpocząć pięć elementów roboczych w puli wątków i mieć każde wywołanie elementu pracy <xref:System.Threading.CountdownEvent.Signal%2A> po jego zakończeniu. Każde wywołanie <xref:System.Threading.CountdownEvent.Signal%2A> zmniejsza liczbę sygnałów o 1. W wątku głównym wywołanie <xref:System.Threading.CountdownEvent.Wait%2A> zostanie zablokowane, dopóki liczba sygnałów nie będzie równa zero.  
  
> [!NOTE]
> W przypadku kodu, który nie musi współdziałać ze starszymi interfejsami API synchronizacji .NET Framework, rozważ użycie <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów lub <xref:System.Threading.Tasks.Parallel.Invoke%2A> metody dla jeszcze łatwiejszego podejścia do wyznaczania równoległości przyłączania do rozwidlenia.  
  
 <xref:System.Threading.CountdownEvent>ma następujące dodatkowe funkcje:  
  
- Operację oczekiwania można anulować przy użyciu tokenów anulowania.  
  
- Po utworzeniu wystąpienia można zwiększyć jego liczbę sygnałów.  
  
- Wystąpienia mogą być ponownie używane po <xref:System.Threading.CountdownEvent.Wait%2A> zwróceniu przez wywołanie <xref:System.Threading.CountdownEvent.Reset%2A> metody.  
  
- Wystąpienia uwidaczniają <xref:System.Threading.WaitHandle> integrację z innymi interfejsami API synchronizacji .NET Framework, takimi jak <xref:System.Threading.WaitHandle.WaitAll%2A> .  
  
## <a name="basic-usage"></a>Podstawowe użycie  
 Poniższy przykład ilustruje sposób używania elementu z elementem <xref:System.Threading.CountdownEvent> <xref:System.Threading.ThreadPool> roboczym.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent z anulowaniem  
 Poniższy przykład pokazuje, jak anulować operację oczekiwania przy <xref:System.Threading.CountdownEvent> użyciu tokenu anulowania. Wzorzec podstawowy jest zgodny z modelem dla ujednoliconego anulowania, który został wprowadzony w .NET Framework 4. Aby uzyskać więcej informacji, zobacz [Anulowanie w zarządzanych wątkach](cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Należy pamiętać, że operacja oczekiwania nie anuluje wątków, które je sygnalizujący. Zazwyczaj anulowanie jest stosowane do operacji logicznej i może obejmować oczekiwanie na zdarzenie, a także wszystkie elementy robocze, które trwają synchronizacja. W tym przykładzie każdy element roboczy otrzymuje kopię tego samego tokenu anulowania, aby mógł on odpowiedzieć na żądanie anulowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
