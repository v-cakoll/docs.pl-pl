---
title: ManualResetEvent EventWaitHandle, CountdownEvent,
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c682fbcc09609a9a4e59b29d5c8997a5ae21d2bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266528"
---
# <a name="eventwaithandle-countdownevent-manualresetevent"></a><span data-ttu-id="969fa-102">ManualResetEvent EventWaitHandle, CountdownEvent,</span><span class="sxs-lookup"><span data-stu-id="969fa-102">EventWaitHandle, CountdownEvent, ManualResetEvent</span></span>

<span data-ttu-id="969fa-103">Uchwyty oczekiwania na zdarzenie umożliwiają wątków, aby zsynchronizować działań przez siebie Sygnalizowanie i Oczekiwanie na siebie nawzajem sygnałów.</span><span class="sxs-lookup"><span data-stu-id="969fa-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="969fa-104">Te zdarzenia synchronizacji opierają się na uchwyty oczekiwania na system operacyjny i można podzielić na dwa typy: te, które automatycznie resetować podczas sygnalizowane, które zostaną przywrócone ręcznie.</span><span class="sxs-lookup"><span data-stu-id="969fa-104">These synchronization events are based on operating system wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
<span data-ttu-id="969fa-105">Uchwyty oczekiwania na zdarzenie są przydatne w wielu z tych samych scenariuszy synchronizacji co <xref:System.Threading.Monitor> klasy.</span><span class="sxs-lookup"><span data-stu-id="969fa-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="969fa-106">Uchwyty oczekiwania na zdarzenie często są łatwiejsze w obsłudze niż <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody i oferują większą kontrolę nad sygnalizowanie.</span><span class="sxs-lookup"><span data-stu-id="969fa-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="969fa-107">Uchwyty oczekiwania na zdarzenie o nazwie można również do synchronizowania działań w domenach aplikacji i procesów, podczas gdy monitory są lokalne w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="969fa-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="969fa-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="969fa-108">In this section</span></span>

 [<span data-ttu-id="969fa-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="969fa-109">EventWaitHandle</span></span>](eventwaithandle.md)  
 <span data-ttu-id="969fa-110"><xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Klasa może reprezentować albo automatyczne lub ręczne Resetowanie zdarzenia i albo lokalne lub o nazwie zdarzenia systemowe.</span><span class="sxs-lookup"><span data-stu-id="969fa-110">The <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="969fa-111">ManualResetEvent i ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="969fa-111">ManualResetEvent and ManualResetEventSlim</span></span>](manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="969fa-112"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasa pochodzi od <xref:System.Threading.EventWaitHandle> i reprezentuje lokalne zdarzenia, które muszą zostać zresetowane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="969fa-112">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="969fa-113"><xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> Klasa jest uproszczone, szybciej wersji, który może służyć do zdarzenia w obrębie tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="969fa-113">The <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="969fa-114">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="969fa-114">CountdownEvent</span></span>](countdownevent.md)  
 <span data-ttu-id="969fa-115"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Klasa oferuje uproszczony sposób na implementowanie wzorców równoległości rozwidlenia/scalania w kodzie używa uchwyty oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="969fa-115">The <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  

## <a name="see-also"></a><span data-ttu-id="969fa-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="969fa-116">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [<span data-ttu-id="969fa-117">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="969fa-117">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="969fa-118">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="969fa-118">Managed threading basics</span></span>](managed-threading-basics.md)
