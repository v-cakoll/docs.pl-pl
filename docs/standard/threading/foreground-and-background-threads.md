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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138049"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="2bb85-102">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="2bb85-102">Foreground and Background Threads</span></span>
<span data-ttu-id="2bb85-103">Zarządzany wątek jest wątkiem w tle lub wątkiem pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="2bb85-104">Wątki w tle są takie same jak wątki pierwszego planu z jednym wyjątkiem: wątek w tle nie utrzymuje uruchomionego środowiska wykonywania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2bb85-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="2bb85-105">Po zatrzymaniu wszystkich wątków pierwszego planu w procesie zarządzanym (gdzie plik exe jest zestawem zarządzanym) system zatrzymuje wszystkie wątki w tle i zamyka.</span><span class="sxs-lookup"><span data-stu-id="2bb85-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bb85-106">Gdy środowisko uruchomieniowe zatrzyma wątek w tle, ponieważ trwa zamykanie procesu, w wątku nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2bb85-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="2bb85-107">Jeśli jednak wątki są zatrzymane, ponieważ metoda <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zwalnia domenę aplikacji, <xref:System.Threading.ThreadAbortException> jest generowany zarówno w wątku na pierwszym planie, jak i w tle.</span><span class="sxs-lookup"><span data-stu-id="2bb85-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="2bb85-108">Użyj właściwości <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>, aby określić, czy wątek to tło, czy wątek pierwszego planu czy zmienić jego stan.</span><span class="sxs-lookup"><span data-stu-id="2bb85-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="2bb85-109">Wątek można w dowolnym momencie zmienić na wątek w tle przez ustawienie jego właściwości <xref:System.Threading.Thread.IsBackground%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="2bb85-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2bb85-110">Stan pierwszego planu lub tła wątku nie wpływa na wynik nieobsługiwanego wyjątku w wątku.</span><span class="sxs-lookup"><span data-stu-id="2bb85-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="2bb85-111">W .NET Framework w wersji 2,0, nieobsłużony wyjątek w wątkach na pierwszym planie lub w tle powoduje zakończenie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2bb85-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="2bb85-112">Zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="2bb85-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="2bb85-113">Wątki należące do puli wątków zarządzanych (czyli wątki, których właściwość <xref:System.Threading.Thread.IsThreadPoolThread%2A> jest `true`) są wątkami w tle.</span><span class="sxs-lookup"><span data-stu-id="2bb85-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="2bb85-114">Wszystkie wątki, które wprowadzają zarządzane środowisko wykonawcze z kodu niezarządzanego, są oznaczane jako wątki w tle.</span><span class="sxs-lookup"><span data-stu-id="2bb85-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="2bb85-115">Wszystkie wątki wygenerowane przez tworzenie i uruchamianie nowego obiektu <xref:System.Threading.Thread> są domyślnie wątki pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="2bb85-116">Jeśli użyjesz wątku do monitorowania działania, takiego jak połączenie gniazda, ustaw jej Właściwość <xref:System.Threading.Thread.IsBackground%2A> na `true`, aby wątek nie uniemożliwił przerwania procesu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb85-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bb85-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
