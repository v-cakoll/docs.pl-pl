---
title: ManualResetEvent i ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4949540b9f61e71301647a83a1c05d8b4c941412
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581275"
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="265be-102">ManualResetEvent i ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="265be-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="265be-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które można ręcznie zresetować po zostanie zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="265be-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="265be-104">Ta klasa reprezentuje przypadkiem szczególnym klasy bazowej, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="265be-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="265be-105">Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacji koncepcyjnego dla użycia i funkcje ręczne Resetowanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="265be-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="265be-106">A <xref:System.Threading.ManualResetEvent> obiekt pozostaje sygnałowego aż do jego <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="265be-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="265be-107">Dowolną liczbę oczekujących wątki lub wątki, które oczekiwania na zdarzenie po zostało zasygnalizowane, może być zwolnione, gdy stan obiektu jest sygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="265be-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span>
  
 <span data-ttu-id="265be-108">W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], możesz użyć <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> klasy w celu zapewnienia lepszej wydajności po spodziewane czasy oczekiwania będą bardzo krótkie, a gdy zdarzenie nie przekraczają granice procesu.</span><span class="sxs-lookup"><span data-stu-id="265be-108">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="265be-109"><xref:System.Threading.ManualResetEventSlim> używa zajęty, obracanie przez krótki czas podczas oczekiwania na zdarzenie zostało zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="265be-109"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="265be-110">W przypadku krótkie czasy oczekiwania rotowania może być znacznie mniej kosztowne niż za pomocą uchwytów oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="265be-110">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="265be-111">Jednakże, jeśli zdarzenie nie zasygnalizowane w przedziale czasu, <xref:System.Threading.ManualResetEventSlim> sortuje ponownie do oczekiwania uchwyt wydarzeń.</span><span class="sxs-lookup"><span data-stu-id="265be-111">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="265be-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="265be-112">See also</span></span>

- [<span data-ttu-id="265be-113">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="265be-113">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="265be-114">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="265be-114">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="265be-115">Uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="265be-115">Wait Handles</span></span>](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
- [<span data-ttu-id="265be-116">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="265be-116">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
- [<span data-ttu-id="265be-117">SpinWait</span><span class="sxs-lookup"><span data-stu-id="265be-117">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
- [<span data-ttu-id="265be-118">Semaphore i SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="265be-118">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
