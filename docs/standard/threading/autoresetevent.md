---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które automatycznie po resetuje sygnalizowane po zwalniania pojedynczego wątku oczekiwania. Ta klasa reprezentuje szczególnych przypadkach klasy podstawowej, <xref:System.Threading.EventWaitHandle>. Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacja koncepcyjna wykorzystania i funkcji automatycznego resetowania zdarzeń.  
  
 <xref:System.Threading.AutoResetEvent> Obiektu jest automatycznie zresetować do innych niż zasygnalizowane przez system po jednym oczekiwania wątku został zwolniony. Jeśli nie ma wątków oczekujących, stan obiektu zdarzenie pozostaje sygnałowego. <xref:System.Threading.AutoResetEvent>odpowiada Win32 `CreateEvent` wywołać, określając `false` dla `bManualReset` argumentu.  
  
 Na przykład, który używa <xref:System.Threading.AutoResetEvent>, zobacz [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle, autoresetevent —, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Uchwyty oczekiwania](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
