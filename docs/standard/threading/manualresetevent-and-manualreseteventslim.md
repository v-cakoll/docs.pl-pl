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
ms.openlocfilehash: c85d0c5c291743c6daac549e15d479fcf332235c
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452826"
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="bfb07-102">ManualResetEvent i ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="bfb07-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="bfb07-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które można ręcznie zresetować po zostanie zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="bfb07-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="bfb07-104">Ta klasa reprezentuje przypadkiem szczególnym klasy bazowej, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfb07-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bfb07-105">Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacji koncepcyjnego dla użycia i funkcje ręczne Resetowanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb07-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="bfb07-106">A <xref:System.Threading.ManualResetEvent> obiekt pozostaje sygnałowego aż do jego <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="bfb07-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="bfb07-107">Dowolną liczbę oczekujących wątki lub wątki, które oczekiwania na zdarzenie po zostało zasygnalizowane, może być zwolnione, gdy stan obiektu jest sygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="bfb07-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span>
  
 <span data-ttu-id="bfb07-108">W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], możesz użyć <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> klasy w celu zapewnienia lepszej wydajności po spodziewane czasy oczekiwania będą bardzo krótkie, a gdy zdarzenie nie przekraczają granice procesu.</span><span class="sxs-lookup"><span data-stu-id="bfb07-108">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="bfb07-109"><xref:System.Threading.ManualResetEventSlim> używa zajęty, obracanie przez krótki czas podczas oczekiwania na zdarzenie zostało zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="bfb07-109"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="bfb07-110">W przypadku krótkie czasy oczekiwania rotowania może być znacznie mniej kosztowne niż za pomocą uchwytów oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="bfb07-110">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="bfb07-111">Jednakże, jeśli zdarzenie nie zasygnalizowane w przedziale czasu, <xref:System.Threading.ManualResetEventSlim> sortuje ponownie do oczekiwania uchwyt wydarzeń.</span><span class="sxs-lookup"><span data-stu-id="bfb07-111">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb07-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfb07-112">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="bfb07-113">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="bfb07-113">AutoResetEvent</span></span>](autoresetevent.md)  
- [<span data-ttu-id="bfb07-114">SpinWait</span><span class="sxs-lookup"><span data-stu-id="bfb07-114">SpinWait</span></span>](spinwait.md)  
- [<span data-ttu-id="bfb07-115">Semaphore i SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="bfb07-115">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)
- [<span data-ttu-id="bfb07-116">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="bfb07-116">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [<span data-ttu-id="bfb07-117">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="bfb07-117">Threading objects and features</span></span>](threading-objects-and-features.md)  
- [<span data-ttu-id="bfb07-118">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="bfb07-118">Threading</span></span>](index.md)  
