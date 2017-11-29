---
title: contextSwitchDeadlock MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e67c5c47dbe95d7c2b804f0ae87200db489d0306
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="4cd62-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="4cd62-102">contextSwitchDeadlock MDA</span></span>
<span data-ttu-id="4cd62-103">`contextSwitchDeadlock` Zarządzany Asystent debugowania (MDA) została aktywowana po wykryciu zakleszczenie podczas próby przejścia kontekstu COM.</span><span class="sxs-lookup"><span data-stu-id="4cd62-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4cd62-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="4cd62-104">Symptoms</span></span>  
 <span data-ttu-id="4cd62-105">Najbardziej typowe objaw jest wywołanie niezarządzane składnika modelu COM z kodu zarządzanego nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="4cd62-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="4cd62-106">Kolejnym objawem może być użycie pamięci zwiększa się w czasie.</span><span class="sxs-lookup"><span data-stu-id="4cd62-106">Another symptom is memory usage increasing over time.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4cd62-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="4cd62-107">Cause</span></span>  
 <span data-ttu-id="4cd62-108">Najbardziej prawdopodobną przyczyną jest to, że wątku jednowątkowego apartamentu (STA) nie jest przekazywanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4cd62-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="4cd62-109">Wątku STA. jest albo oczekiwania bez przekazywania komunikatów lub operacji długie i nie zezwala na wiadomości w kolejce pompa.</span><span class="sxs-lookup"><span data-stu-id="4cd62-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>  
  
 <span data-ttu-id="4cd62-110">Użycie pamięci zwiększa się w czasie jest spowodowany przez wątek finalizatora próba wywołania `Release` niezarządzane COM składnika i składnik ten nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="4cd62-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="4cd62-111">Zapobiega to odzyskiwanie inne obiekty finalizatora.</span><span class="sxs-lookup"><span data-stu-id="4cd62-111">This prevents the finalizer from reclaiming other objects.</span></span>  
  
 <span data-ttu-id="4cd62-112">Jest domyślnie pozostaje tryb komórek jednowątkowych model wątkowy wątku głównego aplikacji konsoli języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4cd62-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="4cd62-113">To zdarzenie MDA jest włączone, jeśli wątku STA. używa współdziałanie COM bezpośrednio lub pośrednio przez środowisko uruchomieniowe języka wspólnego lub formantu innych firm.</span><span class="sxs-lookup"><span data-stu-id="4cd62-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="4cd62-114">Aby uniknąć aktywowanie to zdarzenie MDA w aplikacji konsoli języka Visual Basic, zastosuj <xref:System.MTAThreadAttribute> atrybut do głównej metody lub zmodyfikować aplikację tak, by przekazywać komunikaty.</span><span class="sxs-lookup"><span data-stu-id="4cd62-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>  
  
 <span data-ttu-id="4cd62-115">Jest to możliwe, że to zdarzenie MDA do fałszywie aktywowany, gdy są spełnione wszystkie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="4cd62-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="4cd62-116">Aplikacja tworzy składniki modelu COM z wątki STA bezpośrednio lub pośrednio do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4cd62-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>  
  
-   <span data-ttu-id="4cd62-117">Aplikacja została zatrzymana w debugerze, a użytkownik nadal aplikacji lub wykonać operacji kroku.</span><span class="sxs-lookup"><span data-stu-id="4cd62-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>  
  
-   <span data-ttu-id="4cd62-118">Nie włączono debugowanie niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="4cd62-118">Unmanaged debugging is not enabled.</span></span>  
  
 <span data-ttu-id="4cd62-119">Aby ustalić, czy MDA fałszywie aktywowana, wyłącz wszystkie punkty przerwania, ponownie uruchom aplikację i zezwolenie na uruchamianie bez zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="4cd62-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="4cd62-120">Jeśli nie włączono MDA, prawdopodobnie początkowej aktywacji była wartość false.</span><span class="sxs-lookup"><span data-stu-id="4cd62-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="4cd62-121">W takim przypadku należy wyłączyć MDA w celu uniknięcia konfliktów z sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="4cd62-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cd62-122">To zdarzenie MDA znajduje się w domyślnym zestawem dla [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="4cd62-122">This MDA is in the default set for [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and later versions.</span></span> <span data-ttu-id="4cd62-123">Podczas procesu hostingu jest włączone w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], nie można wyłączyć mda ustawionych w domyślnym.</span><span class="sxs-lookup"><span data-stu-id="4cd62-123">When the hosting process is enabled in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], you cannot disable MDAs that are in the default set.</span></span> <span data-ttu-id="4cd62-124">Proces hostingu jest włączona domyślnie, więc musi być jawnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="4cd62-124">The hosting process is enabled by default, so it must be explicitly disabled.</span></span> <span data-ttu-id="4cd62-125">Aby dowiedzieć się, jak wyłączyć mda, zobacz "Włączanie i wyłączanie mda" w [diagnozowanie problemów z Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="4cd62-125">For information about how to disable MDAs, see "Enabling and Disabling MDAs" in [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4cd62-126">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="4cd62-126">Resolution</span></span>  
 <span data-ttu-id="4cd62-127">Wykonaj COM zasady dotyczące przekazywanie komunikatów STA.</span><span class="sxs-lookup"><span data-stu-id="4cd62-127">Follow COM rules regarding STA message pumping.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4cd62-128">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4cd62-128">Effect on the Runtime</span></span>  
 <span data-ttu-id="4cd62-129">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="4cd62-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="4cd62-130">Zwraca tylko dane o kontekstach COM.</span><span class="sxs-lookup"><span data-stu-id="4cd62-130">It only reports data about COM contexts.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4cd62-131">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4cd62-131">Output</span></span>  
 <span data-ttu-id="4cd62-132">Komunikat opisujący bieżący kontekst i kontekst docelowy.</span><span class="sxs-lookup"><span data-stu-id="4cd62-132">A message describing the current context and the target context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4cd62-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4cd62-133">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cd62-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cd62-134">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="4cd62-135">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="4cd62-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="4cd62-136">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="4cd62-136">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
