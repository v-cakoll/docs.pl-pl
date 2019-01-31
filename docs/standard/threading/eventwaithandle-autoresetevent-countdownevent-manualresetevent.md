---
title: EventWaitHandle, CountdownEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fafdc2a360038021217d9a42406c971b1094678b
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479935"
---
# <a name="eventwaithandle-countdownevent"></a>EventWaitHandle, CountdownEvent

Uchwyty oczekiwania na zdarzenie umożliwiają wątków, aby zsynchronizować działań przez siebie Sygnalizowanie i Oczekiwanie na siebie nawzajem sygnałów. Te zdarzenia synchronizacji opierają się na uchwyty oczekiwania na system operacyjny i można podzielić na dwa typy: te, które automatycznie resetować podczas sygnalizowane, które zostaną przywrócone ręcznie.  
  
Uchwyty oczekiwania na zdarzenie są przydatne w wielu z tych samych scenariuszy synchronizacji co <xref:System.Threading.Monitor> klasy. Uchwyty oczekiwania na zdarzenie często są łatwiejsze w obsłudze niż <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody i oferują większą kontrolę nad sygnalizowanie. Uchwyty oczekiwania na zdarzenie o nazwie można również do synchronizowania działań w domenach aplikacji i procesów, podczas gdy monitory są lokalne w domenie aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji

 [EventWaitHandle](eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Klasa może reprezentować albo automatyczne lub ręczne Resetowanie zdarzenia i albo lokalne lub o nazwie zdarzenia systemowe.  
  
 [CountdownEvent](countdownevent.md)  
 <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Klasa oferuje uproszczony sposób na implementowanie wzorców równoległości rozwidlenia/scalania w kodzie używa uchwyty oczekiwania.  

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Zarządzana wątkowość — podstawy](managed-threading-basics.md)
