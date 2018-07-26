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
ms.openlocfilehash: c1785ce223f0dcd4da7ea6ef9fa3a3e897a39dca
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143521"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które automatycznie po resetuje sygnalizowane po przy zwalnianiu pojedynczego wątku oczekiwania. Ta klasa reprezentuje przypadkiem szczególnym klasy bazowej, <xref:System.Threading.EventWaitHandle>. Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacji koncepcyjnego dla użycia i funkcji automatycznego resetowania zdarzeń.  
  
 <xref:System.Threading.AutoResetEvent> Obiekt jest automatycznie ustawiany na zasygnalizowane przez system po udostępnieniu pojedynczego wątku oczekiwania. Jeśli żadne wątki oczekujące, stan z obiektem zdarzenia pozostaje sygnałowego. <xref:System.Threading.AutoResetEvent> odnosi się do systemu Win32 `CreateEvent` wywołać, określając `false` dla `bManualReset` argumentu.  
  
 Aby uzyskać przykład, który używa <xref:System.Threading.AutoResetEvent>, zobacz <xref:System.Threading.Monitor>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Uchwyty oczekiwania](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
