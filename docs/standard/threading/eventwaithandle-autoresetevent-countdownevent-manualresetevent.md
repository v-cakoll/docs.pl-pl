---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f61e614696e731a85a030e34aa4356137d9000d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882350"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Uchwyty oczekiwania na zdarzenie umożliwiają wątków, aby zsynchronizować działań przez siebie Sygnalizowanie i Oczekiwanie na siebie nawzajem sygnałów. Te zdarzenia synchronizacji są oparte na Win32 uchwytami oczekiwania i można podzielić na dwa typy: te, które automatycznie resetować podczas sygnalizowane, które zostaną przywrócone ręcznie.  
  
 Uchwyty oczekiwania na zdarzenie są przydatne w wielu z tych samych scenariuszy synchronizacji co <xref:System.Threading.Monitor> klasy. Uchwyty oczekiwania na zdarzenie często są łatwiejsze w obsłudze niż <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody i oferują większą kontrolę nad sygnalizowanie. Uchwyty oczekiwania na zdarzenie o nazwie można również do synchronizowania działań w domenach aplikacji i procesów, podczas gdy monitory są lokalne w domenie aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> Klasa może reprezentować albo automatyczne lub ręczne Resetowanie zdarzenia i albo lokalne lub o nazwie zdarzenia systemowe.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> Klasa pochodzi od <xref:System.Threading.EventWaitHandle> i reprezentuje zdarzenie lokalnego, który przywraca automatycznie.  
  
 [ManualResetEvent i ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> Klasa pochodzi od <xref:System.Threading.EventWaitHandle> i reprezentuje lokalne zdarzenia, które muszą zostać zresetowane ręcznie. <xref:System.Threading.ManualResetEventSlim> Klasa jest uproszczone, szybciej wersji, który może służyć do zdarzenia w obrębie tego samego procesu.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> Klasa oferuje uproszczony sposób na implementowanie wzorców równoległości rozwidlenia/scalania w kodzie używa uchwyty oczekiwania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Uchwyty oczekiwania](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> Klasa jest klasą bazową dla <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, i <xref:System.Threading.Mutex> klasy. Zawiera metody statyczne takie jak <xref:System.Threading.WaitHandle.SignalAndWait%2A> i <xref:System.Threading.WaitHandle.WaitAll%2A> są przydatne podczas pracy ze wszystkimi typami dojść oczekiwania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.EventWaitHandle>  
- <xref:System.Threading.WaitHandle>  
- <xref:System.Threading.AutoResetEvent>  
- <xref:System.Threading.ManualResetEvent>  
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
