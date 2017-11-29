---
title: "Wątki pierwszego planu i tła"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="e812c-102">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="e812c-102">Foreground and Background Threads</span></span>
<span data-ttu-id="e812c-103">Zarządzane wątek jest wątku w tle lub wątku pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="e812c-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="e812c-104">Wątki w tle są takie same jak wątki pierwszoplanowe z jednym wyjątkiem: wątku w tle nie przechowuje zarządzanego środowiska wykonawczego uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e812c-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="e812c-105">Po w procesie zarządzanych (gdzie plik .exe jest zestaw zarządzany) zostały zatrzymane wszystkie wątki pierwszego planu, system zatrzymuje wszystkie wątki w tle i zamyka.</span><span class="sxs-lookup"><span data-stu-id="e812c-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e812c-106">Środowisko uruchomieniowe zatrzymania wątku w tle, ponieważ trwa zamykanie procesu, nie jest wyjątek w wątku.</span><span class="sxs-lookup"><span data-stu-id="e812c-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="e812c-107">Jednak gdy wątki są zatrzymane, ponieważ <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda zwalnia domeny aplikacji <xref:System.Threading.ThreadAbortException> jest zgłaszany w wątkach tła i pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="e812c-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="e812c-108">Użyj <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> właściwości, aby określić, czy wątek jest tło lub wątku pierwszego planu lub zmienić jego stan.</span><span class="sxs-lookup"><span data-stu-id="e812c-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="e812c-109">Wątek, który można zmienić na wątku w tle w dowolnym momencie przez ustawienie jej <xref:System.Threading.Thread.IsBackground%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="e812c-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e812c-110">Pierwszym planie lub w tle stan wątku nie ma wpływu na wynik nieobsługiwany wyjątek w wątku.</span><span class="sxs-lookup"><span data-stu-id="e812c-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="e812c-111">Wystąpił nieobsługiwany wyjątek w wątkach na pierwszym planie lub w tle w programie .NET Framework w wersji 2.0, powoduje Kończenie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e812c-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="e812c-112">Zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="e812c-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="e812c-113">Wątków, które należą do puli wątków zarządzanych (to znaczy, których wątki <xref:System.Threading.Thread.IsThreadPoolThread%2A> jest właściwość `true`) są wątki w tle.</span><span class="sxs-lookup"><span data-stu-id="e812c-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="e812c-114">Wprowadź zarządzanego środowiska wykonawczego z kodem niezarządzanym wszystkie wątki są oznaczone jako wątki w tle.</span><span class="sxs-lookup"><span data-stu-id="e812c-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="e812c-115">Wszystkie wątki generowane przez tworzenie i uruchamianie nowej <xref:System.Threading.Thread> obiektu są przez wątki pierwszoplanowe domyślne.</span><span class="sxs-lookup"><span data-stu-id="e812c-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="e812c-116">Jeśli wątek służą do monitorowania działania, takie jak połączenia gniazda, ustaw jej <xref:System.Threading.Thread.IsBackground%2A> właściwości `true` , dzięki czemu wątek nie uniemożliwia zakończenie procesu.</span><span class="sxs-lookup"><span data-stu-id="e812c-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e812c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e812c-117">See Also</span></span>  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
