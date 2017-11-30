---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Uchwyty oczekiwania na zdarzenie Zezwalaj wątków, aby zsynchronizować działań przez siebie sygnalizowania i Oczekiwanie na sygnały siebie nawzajem. Te zdarzenia synchronizacji są oparte na uchwyty oczekiwania Win32 i można podzielić na dwa typy: te, które automatycznie resetować podczas sygnalizowane oraz te, które są resetowane ręcznie.  
  
 Uchwyty oczekiwania na zdarzenie są przydatne w wielu z tych samych operacji synchronizacji jako <xref:System.Threading.Monitor> klasy. Uchwyty oczekiwania na zdarzenie są często łatwe w użyciu niż <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metod i ich oferują lepszą kontrolę nad sygnalizowania. Uchwyty oczekiwania na zdarzenie o nazwie można również zsynchronizować działań w domenach aplikacji i procesów, monitory są lokalne dla domeny aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> Klasa może reprezentować albo automatyczne lub ręczne Resetowanie zdarzenia i albo lokalnego lub o nazwie zdarzeń systemowych.  
  
 [Autoresetevent —](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> Pochodną klasy <xref:System.Threading.EventWaitHandle> i reprezentuje lokalnym zdarzeniem, które automatycznie resetuje.  
  
 [ManualResetEvent i ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> Pochodną klasy <xref:System.Threading.EventWaitHandle> i reprezentuje lokalnym zdarzeniem, które musi zostać zresetowany ręcznie. <xref:System.Threading.ManualResetEventSlim> Klasa jest niewielka, szybsze wersji, która może służyć do zdarzeń w tym samym procesie.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> Klasa umożliwia uproszczonej Implementowanie wzorców równoległości rozwidlenia/sprzężenia w kodzie używa uchwyty oczekiwania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Uchwyty oczekiwania](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> Klasa jest klasą bazową dla <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, i <xref:System.Threading.Mutex> klasy. Zawiera metody statyczne takie jak <xref:System.Threading.WaitHandle.SignalAndWait%2A> i <xref:System.Threading.WaitHandle.WaitAll%2A> są przydatne podczas pracy ze wszystkimi typami uchwyty oczekiwania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
