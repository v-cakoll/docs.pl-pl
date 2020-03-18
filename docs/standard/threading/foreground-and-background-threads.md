---
title: Wątki pierwszego planu i tła
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 9e93f07b3b84264373db0317919b6ee519c8127c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138049"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="77f5f-102">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="77f5f-102">Foreground and Background Threads</span></span>
<span data-ttu-id="77f5f-103">Wątek zarządzany jest wątkiem tła lub wątku pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="77f5f-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="77f5f-104">Wątki w tle są identyczne z wątków pierwszego planu z jednym wyjątkiem: wątek w tle nie prowadzi zarządzanego środowiska wykonawczego uruchomione.</span><span class="sxs-lookup"><span data-stu-id="77f5f-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="77f5f-105">Po zatrzymaniu wszystkich wątków pierwszego planu w procesie zarządzanym (gdzie plik exe jest zarządzanym zestawem), system zatrzymuje wszystkie wątki w tle i zamyka.</span><span class="sxs-lookup"><span data-stu-id="77f5f-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77f5f-106">Gdy środowiska uruchomieniowego zatrzymuje wątek w tle, ponieważ proces jest zamykany, nie wyjątek w wątku.</span><span class="sxs-lookup"><span data-stu-id="77f5f-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="77f5f-107">Jednak gdy wątki są <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zatrzymane, ponieważ metoda zwalnia <xref:System.Threading.ThreadAbortException> domeny aplikacji, a jest generowany zarówno w wątkach pierwszego planu i tła.</span><span class="sxs-lookup"><span data-stu-id="77f5f-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="77f5f-108">Użyj <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> właściwości, aby ustalić, czy wątek jest tłem lub wątkiem pierwszego planu, czy zmienić jego stan.</span><span class="sxs-lookup"><span data-stu-id="77f5f-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="77f5f-109">Wątek można zmienić na wątek w tle w <xref:System.Threading.Thread.IsBackground%2A> dowolnym `true`momencie, ustawiając jego właściwość na .</span><span class="sxs-lookup"><span data-stu-id="77f5f-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77f5f-110">Pierwszy plan lub stan tła wątku nie ma wpływu na wynik nieobsługiwanego wyjątku w wątku.</span><span class="sxs-lookup"><span data-stu-id="77f5f-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="77f5f-111">W .NET Framework w wersji 2.0 nieobsługiwany wyjątek w wątkach pierwszego planu lub tła powoduje zakończenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77f5f-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="77f5f-112">Zobacz [wyjątki w wątkach zarządzanych](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="77f5f-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="77f5f-113">Wątki, które należą do puli wątków zarządzanych (czyli wątków, których <xref:System.Threading.Thread.IsThreadPoolThread%2A> właściwość jest `true`) są wątki w tle.</span><span class="sxs-lookup"><span data-stu-id="77f5f-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="77f5f-114">Wszystkie wątki, które wchodzą do środowiska wykonawczego zarządzanego z kodu niezarządzanego są oznaczone jako wątki w tle.</span><span class="sxs-lookup"><span data-stu-id="77f5f-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="77f5f-115">Wszystkie wątki generowane przez tworzenie <xref:System.Threading.Thread> i uruchamianie nowego obiektu są domyślnie wątków pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="77f5f-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="77f5f-116">Jeśli używasz wątku do monitorowania działania, takich jak <xref:System.Threading.Thread.IsBackground%2A> połączenie `true` gniazda, należy ustawić jego właściwość tak, aby wątek nie uniemożliwia zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="77f5f-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f5f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77f5f-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
