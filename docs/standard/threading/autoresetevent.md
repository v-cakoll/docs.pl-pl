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
ms.openlocfilehash: 519776b5c1c237deb520476384495b8dd96a4e39
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039286"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które automatycznie po resetuje sygnalizowane po przy zwalnianiu pojedynczego wątku oczekiwania. Ta klasa reprezentuje przypadkiem szczególnym klasy bazowej, <xref:System.Threading.EventWaitHandle>. Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacji koncepcyjnego dla użycia i funkcji automatycznego resetowania zdarzeń.  
  
 <xref:System.Threading.AutoResetEvent> Obiekt jest automatycznie ustawiany na zasygnalizowane przez system po udostępnieniu pojedynczego wątku oczekiwania. Jeśli żadne wątki oczekujące, stan z obiektem zdarzenia pozostaje sygnałowego.
  
 Aby uzyskać przykład, który używa <xref:System.Threading.AutoResetEvent>, zobacz <xref:System.Threading.Monitor>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)  
- [Wątkowość](index.md)  
