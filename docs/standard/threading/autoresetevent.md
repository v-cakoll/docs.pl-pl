---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ab06993eed4b39746875a6ef3ebfad5edbd2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581706"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które automatycznie po resetuje sygnalizowane po zwalniania pojedynczego wątku oczekiwania. Ta klasa reprezentuje szczególnych przypadkach klasy podstawowej, <xref:System.Threading.EventWaitHandle>. Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacja koncepcyjna wykorzystania i funkcji automatycznego resetowania zdarzeń.  
  
 <xref:System.Threading.AutoResetEvent> Obiektu jest automatycznie zresetować do innych niż zasygnalizowane przez system po jednym oczekiwania wątku został zwolniony. Jeśli nie ma wątków oczekujących, stan obiektu zdarzenie pozostaje sygnałowego. <xref:System.Threading.AutoResetEvent> odpowiada Win32 `CreateEvent` wywołać, określając `false` dla `bManualReset` argumentu.  
  
 Na przykład, który używa <xref:System.Threading.AutoResetEvent>, zobacz [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Uchwyty oczekiwania](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
