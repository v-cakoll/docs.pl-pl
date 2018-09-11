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
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260152"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="9da3b-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="9da3b-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="9da3b-103">Uchwyty oczekiwania na zdarzenie umożliwiają wątków, aby zsynchronizować działań przez siebie Sygnalizowanie i Oczekiwanie na siebie nawzajem sygnałów.</span><span class="sxs-lookup"><span data-stu-id="9da3b-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="9da3b-104">Te zdarzenia synchronizacji są oparte na Win32 uchwytami oczekiwania i można podzielić na dwa typy: te, które automatycznie resetować podczas sygnalizowane, które zostaną przywrócone ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9da3b-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="9da3b-105">Uchwyty oczekiwania na zdarzenie są przydatne w wielu z tych samych scenariuszy synchronizacji co <xref:System.Threading.Monitor> klasy.</span><span class="sxs-lookup"><span data-stu-id="9da3b-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="9da3b-106">Uchwyty oczekiwania na zdarzenie często są łatwiejsze w obsłudze niż <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody i oferują większą kontrolę nad sygnalizowanie.</span><span class="sxs-lookup"><span data-stu-id="9da3b-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="9da3b-107">Uchwyty oczekiwania na zdarzenie o nazwie można również do synchronizowania działań w domenach aplikacji i procesów, podczas gdy monitory są lokalne w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9da3b-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9da3b-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9da3b-108">In This Section</span></span>  
 [<span data-ttu-id="9da3b-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="9da3b-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="9da3b-110"><xref:System.Threading.EventWaitHandle> Klasa może reprezentować albo automatyczne lub ręczne Resetowanie zdarzenia i albo lokalne lub o nazwie zdarzenia systemowe.</span><span class="sxs-lookup"><span data-stu-id="9da3b-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="9da3b-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="9da3b-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="9da3b-112"><xref:System.Threading.AutoResetEvent> Klasa pochodzi od <xref:System.Threading.EventWaitHandle> i reprezentuje zdarzenie lokalnego, który przywraca automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9da3b-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="9da3b-113">ManualResetEvent i ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="9da3b-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="9da3b-114"><xref:System.Threading.ManualResetEvent> Klasa pochodzi od <xref:System.Threading.EventWaitHandle> i reprezentuje lokalne zdarzenia, które muszą zostać zresetowane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9da3b-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="9da3b-115"><xref:System.Threading.ManualResetEventSlim> Klasa jest uproszczone, szybciej wersji, który może służyć do zdarzenia w obrębie tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="9da3b-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="9da3b-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="9da3b-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="9da3b-117"><xref:System.Threading.CountdownEvent> Klasa oferuje uproszczony sposób na implementowanie wzorców równoległości rozwidlenia/scalania w kodzie używa uchwyty oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="9da3b-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9da3b-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9da3b-118">Related Sections</span></span>  
 [<span data-ttu-id="9da3b-119">Uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="9da3b-119">Wait Handles</span></span>](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="9da3b-120"><xref:System.Threading.WaitHandle> Klasa jest klasą bazową dla <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, i <xref:System.Threading.Mutex> klasy.</span><span class="sxs-lookup"><span data-stu-id="9da3b-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="9da3b-121">Zawiera metody statyczne takie jak <xref:System.Threading.WaitHandle.SignalAndWait%2A> i <xref:System.Threading.WaitHandle.WaitAll%2A> są przydatne podczas pracy ze wszystkimi typami dojść oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="9da3b-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da3b-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9da3b-122">See also</span></span>

- <xref:System.Threading.EventWaitHandle>  
- <xref:System.Threading.WaitHandle>  
- <xref:System.Threading.AutoResetEvent>  
- <xref:System.Threading.ManualResetEvent>  
- [<span data-ttu-id="9da3b-123">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="9da3b-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="9da3b-124">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="9da3b-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
