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
ms.openlocfilehash: 543853f581436a5fb7e5c897012b99bef20dc289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="a630d-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="a630d-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="a630d-103">Uchwyty oczekiwania na zdarzenie Zezwalaj wątków, aby zsynchronizować działań przez siebie sygnalizowania i Oczekiwanie na sygnały siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="a630d-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="a630d-104">Te zdarzenia synchronizacji są oparte na uchwyty oczekiwania Win32 i można podzielić na dwa typy: te, które automatycznie resetować podczas sygnalizowane oraz te, które są resetowane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a630d-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="a630d-105">Uchwyty oczekiwania na zdarzenie są przydatne w wielu z tych samych operacji synchronizacji jako <xref:System.Threading.Monitor> klasy.</span><span class="sxs-lookup"><span data-stu-id="a630d-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="a630d-106">Uchwyty oczekiwania na zdarzenie są często łatwe w użyciu niż <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metod i ich oferują lepszą kontrolę nad sygnalizowania.</span><span class="sxs-lookup"><span data-stu-id="a630d-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="a630d-107">Uchwyty oczekiwania na zdarzenie o nazwie można również zsynchronizować działań w domenach aplikacji i procesów, monitory są lokalne dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a630d-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a630d-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a630d-108">In This Section</span></span>  
 [<span data-ttu-id="a630d-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="a630d-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="a630d-110"><xref:System.Threading.EventWaitHandle> Klasa może reprezentować albo automatyczne lub ręczne Resetowanie zdarzenia i albo lokalnego lub o nazwie zdarzeń systemowych.</span><span class="sxs-lookup"><span data-stu-id="a630d-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="a630d-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="a630d-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="a630d-112"><xref:System.Threading.AutoResetEvent> Pochodną klasy <xref:System.Threading.EventWaitHandle> i reprezentuje lokalnym zdarzeniem, które automatycznie resetuje.</span><span class="sxs-lookup"><span data-stu-id="a630d-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="a630d-113">ManualResetEvent i ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="a630d-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="a630d-114"><xref:System.Threading.ManualResetEvent> Pochodną klasy <xref:System.Threading.EventWaitHandle> i reprezentuje lokalnym zdarzeniem, które musi zostać zresetowany ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a630d-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="a630d-115"><xref:System.Threading.ManualResetEventSlim> Klasa jest niewielka, szybsze wersji, która może służyć do zdarzeń w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="a630d-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="a630d-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="a630d-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="a630d-117"><xref:System.Threading.CountdownEvent> Klasa umożliwia uproszczonej Implementowanie wzorców równoległości rozwidlenia/sprzężenia w kodzie używa uchwyty oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="a630d-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a630d-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a630d-118">Related Sections</span></span>  
 [<span data-ttu-id="a630d-119">Uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="a630d-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="a630d-120"><xref:System.Threading.WaitHandle> Klasa jest klasą bazową dla <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, i <xref:System.Threading.Mutex> klasy.</span><span class="sxs-lookup"><span data-stu-id="a630d-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="a630d-121">Zawiera metody statyczne takie jak <xref:System.Threading.WaitHandle.SignalAndWait%2A> i <xref:System.Threading.WaitHandle.WaitAll%2A> są przydatne podczas pracy ze wszystkimi typami uchwyty oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="a630d-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a630d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a630d-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="a630d-123">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="a630d-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="a630d-124">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="a630d-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
