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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcedd478ee1eb89c11dc9535b1d2ffe843d0f658
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868540"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="85909-102">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="85909-102">Foreground and Background Threads</span></span>
<span data-ttu-id="85909-103">Wątek jest wątku w tle lub wątku na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="85909-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="85909-104">Wątków w tle są takie same, wątki pierwszoplanowe z jednym wyjątkiem: wątku w tle nie przechowuje zarządzanym środowisku wykonywania uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="85909-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="85909-105">Gdy wszystkie wątki pierwszoplanowe zostały zatrzymane w ramach procesu zarządzanego (gdzie plik .exe jest zarządzanym zestawem), system zatrzymuje wszystkich wątków w tle i zamyka.</span><span class="sxs-lookup"><span data-stu-id="85909-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85909-106">Środowisko uruchomieniowe zatrzymania wątku w tle, ponieważ trwa zamykanie procesu, jest zgłaszany żaden wyjątek w wątku.</span><span class="sxs-lookup"><span data-stu-id="85909-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="85909-107">Jednak gdy wątki są zatrzymane, ponieważ <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda zwalnia domeny aplikacji <xref:System.Threading.ThreadAbortException> jest zgłaszany w wątki pierwszego planu i tła.</span><span class="sxs-lookup"><span data-stu-id="85909-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="85909-108">Użyj <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> właściwości, aby określić, czy wątek jest tło lub wątku na pierwszym planie lub zmienić jego stan.</span><span class="sxs-lookup"><span data-stu-id="85909-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="85909-109">Wątek, który można zmienić na wątku w tle w dowolnym momencie przez ustawienie jego <xref:System.Threading.Thread.IsBackground%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="85909-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85909-110">Pierwszy plan lub tło stan wątku nie ma wpływu na wynik nieobsługiwany wyjątek w wątku.</span><span class="sxs-lookup"><span data-stu-id="85909-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="85909-111">W programie .NET Framework 2.0 nieobsługiwanego wyjątku w wątki pierwszego planu i tła powoduje zakończenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85909-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="85909-112">Zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="85909-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="85909-113">Wątki, które należą do puli wątków zarządzanych (oznacza to, wątki, których <xref:System.Threading.Thread.IsThreadPoolThread%2A> właściwość `true`) są wątków w tle.</span><span class="sxs-lookup"><span data-stu-id="85909-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="85909-114">Wszystkie wątki, które wprowadzać środowiska wykonawczego zarządzanych z niezarządzanego kodu są oznaczone jako wątków w tle.</span><span class="sxs-lookup"><span data-stu-id="85909-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="85909-115">Wszystkie wątki, generowane przez tworzenie i uruchamianie nowego <xref:System.Threading.Thread> obiektu są przez domyślne, wątki pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="85909-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="85909-116">Jeśli używasz wątku monitorować działania, takie jak połączenia z gniazdem, ustawić jej <xref:System.Threading.Thread.IsBackground%2A> właściwość `true` tak, aby wątek nie uniemożliwia zakończenie procesu.</span><span class="sxs-lookup"><span data-stu-id="85909-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85909-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85909-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadAbortException>
