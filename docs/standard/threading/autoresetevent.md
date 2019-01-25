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
ms.openlocfilehash: 70af739bdb90a70a1319354b4964c261e432912b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729960"
---
# <a name="autoresetevent"></a><span data-ttu-id="6c83f-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="6c83f-102">AutoResetEvent</span></span>
<span data-ttu-id="6c83f-103"><xref:System.Threading.AutoResetEvent> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które automatycznie po resetuje sygnalizowane po przy zwalnianiu pojedynczego wątku oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="6c83f-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="6c83f-104">Ta klasa reprezentuje przypadkiem szczególnym klasy bazowej, <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="6c83f-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="6c83f-105">Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacji koncepcyjnego dla użycia i funkcji automatycznego resetowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6c83f-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="6c83f-106"><xref:System.Threading.AutoResetEvent> Obiekt jest automatycznie ustawiany na zasygnalizowane przez system po udostępnieniu pojedynczego wątku oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="6c83f-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="6c83f-107">Jeśli żadne wątki oczekujące, stan z obiektem zdarzenia pozostaje sygnałowego.</span><span class="sxs-lookup"><span data-stu-id="6c83f-107">If no threads are waiting, the event object's state remains signaled.</span></span>
  
 <span data-ttu-id="6c83f-108">Aby uzyskać przykład, który używa <xref:System.Threading.AutoResetEvent>, zobacz <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="6c83f-108">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c83f-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c83f-109">See also</span></span>

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="6c83f-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="6c83f-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [<span data-ttu-id="6c83f-111">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="6c83f-111">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="6c83f-112">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="6c83f-112">Threading</span></span>](index.md)
