---
title: Interfejsy hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616843"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="2768f-102">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2768f-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="2768f-103">W tej sekcji opisano interfejsy, które mogą być używane przez niezarządzane hosty do integrowania środowiska uruchomieniowego języka wspólnego (CLR) z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="2768f-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="2768f-104">Informacje dotyczą .NET Framework w wersji 2,0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="2768f-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="2768f-105">Te interfejsy umożliwiają hostowi kontrolowanie wielu innych aspektów środowiska uruchomieniowego niż było możliwe w wersjach 1,0 i 1,1 i zapewniają znacznie ściślejszą integrację między środowiskiem CLR a modelem wykonywania hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="2768f-106">W .NET Framework w wersji 1,0 i 1,1 model hostingu włączył niezarządzany host do załadowania środowiska CLR do procesu, skonfigurowania pewnych ustawień i otrzymywania powiadomień o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="2768f-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="2768f-107">Ogólnie rzecz biorąc, Host i środowisko CLR działały niezależnie w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="2768f-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="2768f-108">W .NET Framework w wersji 2,0 i nowszych nowe warstwy abstrakcji umożliwiają hostowi udostępnianie wielu zasobów, które są obecnie udostępniane przez typy w zestawie Win32, i poszerzają zestaw funkcji, które mogą być konfigurowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2768f-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2768f-109">In This Section</span></span>  
 [<span data-ttu-id="2768f-110">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-110">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="2768f-111">Zapewnia metodę, która wykonuje wywołanie zwrotne dla zarejestrowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2768f-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="2768f-112">IApartmentCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-112">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="2768f-113">Zapewnia metody tworzenia wywołań zwrotnych w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="2768f-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="2768f-114">IAppDomainBinding — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="2768f-115">Zapewnia metody ustawiania konfiguracji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2768f-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="2768f-116">ICatalogServices, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-116">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="2768f-117">Dostarcza metody dla usług katalogowych.</span><span class="sxs-lookup"><span data-stu-id="2768f-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="2768f-118">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="2768f-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="2768f-119">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="2768f-120">Dostarcza metody, które obsługują komunikację między hostem i środowiskiem CLR o zestawach.</span><span class="sxs-lookup"><span data-stu-id="2768f-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="2768f-121">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="2768f-122">Zarządza listą zestawów, które są ładowane przez środowisko CLR, a nie przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="2768f-123">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="2768f-124">Zapewnia metody do uzyskiwania dostępu do hosta i konfigurowania różnych aspektów środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2768f-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="2768f-125">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="2768f-126">Dostarcza metody, które umożliwiają hostowi kojarzenie zestawu zadań z identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="2768f-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="2768f-127">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-127">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="2768f-128">Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów sterty na potrzeby raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="2768f-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="2768f-129">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-129">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="2768f-130">Dostarcza metody, które umożliwiają hostowi współdziałanie z systemem odzyskiwania pamięci CLR.</span><span class="sxs-lookup"><span data-stu-id="2768f-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="2768f-131">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-131">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="2768f-132">Zapewnia metody dla hosta do szacowania i przekazywania zmian w informacjach o zasadach dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="2768f-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="2768f-133">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-133">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="2768f-134">Umożliwia hostowi blokowanie określonych zarządzanych klas, metod, właściwości i pól z uruchamiania w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2768f-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="2768f-135">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="2768f-136">Implementuje metodę wywołania zwrotnego, która umożliwia hostowi powiadomienie środowiska CLR o stanie określonych żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="2768f-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="2768f-137">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="2768f-138">Umożliwia hostowi zgłaszanie warunków ciśnienia pamięci przy użyciu podejścia podobnego do `CreateMemoryResourceNotification` funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="2768f-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="2768f-139">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-139">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="2768f-140">Dostarcza metody, które umożliwiają hostowi rejestrowanie i Wyrejestrowywanie wywołań zwrotnych dla zdarzeń CLR.</span><span class="sxs-lookup"><span data-stu-id="2768f-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="2768f-141">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="2768f-142">Dostarcza metody, które umożliwiają hostowi określenie akcji zasad, które mają być podejmowane w przypadku awarii i przekroczeń limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="2768f-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="2768f-143">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="2768f-144">Dostarcza metody, które umożliwiają hostowi pobieranie tożsamości dla zestawu przy użyciu informacji o tożsamości zestawu, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia lub zrozumienia tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2768f-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="2768f-145">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-145">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="2768f-146">Dostarcza metody, które umożliwiają hostowi manipulowanie zestawem zestawów, do których odwołuje się plik lub strumień przy użyciu danych tożsamości zestawu, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia lub zrozumienia tych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2768f-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="2768f-147">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-147">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="2768f-148">Oferuje funkcje podobne do [ICorRuntimeHost](icorruntimehost-interface.md)z dodatkową metodą ustawiania interfejsu sterowania hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-148">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="2768f-149">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-149">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="2768f-150">Zapewnia metody dla hosta do uzyskiwania informacji o żądanych zadaniach i wykrywania zakleszczenii w jego implementacji synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="2768f-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="2768f-151">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-151">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="2768f-152">Dostarcza metody, które umożliwiają hostowi wykonywanie żądań CLR lub dostarczenie do środowiska CLR powiadomienia o skojarzonym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="2768f-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="2768f-153">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="2768f-154">Dostarcza metody, które umożliwiają hostowi jawne żądanie, aby środowisko CLR utworzyło nowe zadanie, pobrać aktualnie wykonywane zadanie i ustawić język geograficzny i kulturę dla zadania.</span><span class="sxs-lookup"><span data-stu-id="2768f-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="2768f-155">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-155">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="2768f-156">Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="2768f-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="2768f-157">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-157">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="2768f-158">Zapewnia metody konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2768f-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="2768f-159">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-159">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="2768f-160">Zapewnia metody uzyskiwania dostępu do puli wątków.</span><span class="sxs-lookup"><span data-stu-id="2768f-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="2768f-161">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-161">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="2768f-162">Zapewnia metody uzyskiwania informacji o stanie usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="2768f-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="2768f-163">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-163">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="2768f-164">Zapewnia metody powiadamiania hosta o blokowaniu i odblokowywaniu wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="2768f-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="2768f-165">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-165">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="2768f-166">Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2768f-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="2768f-167">IGCHost2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-167">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="2768f-168">Udostępnia metodę [SetGCStartupLimitsEx —](igchost2-setgcstartuplimitsex-method.md) , która umożliwia hostowi Ustawianie rozmiaru segmentu wyrzucania elementów bezużytecznych i maksymalnego rozmiaru generacji wynoszącego system wyrzucania elementów bezużytecznych do wartości większej niż `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="2768f-168">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="2768f-169">IGCHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-169">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="2768f-170">Zapewnia metodę, która umożliwia modułowi wyrzucania elementów bezużytecznych żądanie zmiany limitów pamięci wirtualnej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="2768f-171">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-171">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="2768f-172">Zapewnia metody uczestnictwa w planowaniu wątków, które w przeciwnym razie byłyby blokowane do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2768f-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="2768f-173">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-173">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="2768f-174">Dostarcza metody, które umożliwiają hostowi określenie zestawów zestawów, które powinny być ładowane przez środowisko CLR lub przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="2768f-175">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-175">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="2768f-176">Dostarcza metody, które umożliwiają hostowi załadowanie zestawów i modułów niezależnie od środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2768f-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="2768f-177">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-177">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="2768f-178">Przedstawia reprezentację zdarzenia autoresetowania zaimplementowanego przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="2768f-179">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-179">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="2768f-180">Zapewnia metody konfigurowania ładowania zestawów i określania interfejsów hostingu obsługiwanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="2768f-181">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-181">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="2768f-182">Służy jako reprezentacja hosta sekcji krytycznej dla wątków.</span><span class="sxs-lookup"><span data-stu-id="2768f-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="2768f-183">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-183">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="2768f-184">Dostarcza metody, które powiadamiają hosta zdarzeń w mechanizmie wyrzucania elementów bezużytecznych zaimplementowane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="2768f-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="2768f-185">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-185">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="2768f-186">Dostarcza metody, które umożliwiają współpracującie środowiska CLR z portami zakończenia we/wy dostarczonymi przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="2768f-187">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-187">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="2768f-188">Dostarcza metody dla środowiska CLR do żądania szczegółowych alokacji ze sterty za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="2768f-189">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-189">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="2768f-190">Zapewnia implementację hosta reprezentacji zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="2768f-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="2768f-191">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-191">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="2768f-192">Zapewnia metody środowiska CLR do przydzielenia żądań pamięci wirtualnej za pośrednictwem hosta zamiast używania standardowych funkcji pamięci wirtualnej Win32.</span><span class="sxs-lookup"><span data-stu-id="2768f-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="2768f-193">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-193">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="2768f-194">Dostarcza metody, które powiadamiają hosta o akcjach wykonywanych przez środowisko CLR w przypadku przerwań, przekroczeń limitu czasu lub niepowodzeń.</span><span class="sxs-lookup"><span data-stu-id="2768f-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="2768f-195">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-195">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="2768f-196">Włącza środowisko CLR do obsługi informacji kontekstu zabezpieczeń implementowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="2768f-197">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-197">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="2768f-198">Zapewnia metody umożliwiające dostęp do i kontrolę nad kontekstem zabezpieczeń aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="2768f-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="2768f-199">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-199">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="2768f-200">Przedstawia reprezentację semafora zaimplementowanego przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2768f-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="2768f-201">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-201">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="2768f-202">Zapewnia metody dla środowiska CLR do tworzenia elementów pierwotnych synchronizacji przez wywołanie hosta zamiast korzystania z funkcji synchronizacji Win32.</span><span class="sxs-lookup"><span data-stu-id="2768f-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="2768f-203">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-203">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="2768f-204">Zapewnia metody umożliwiające komunikację środowiska CLR z hostem w celu zarządzania zadaniami.</span><span class="sxs-lookup"><span data-stu-id="2768f-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="2768f-205">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-205">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="2768f-206">Zapewnia metody umożliwiające współdziałanie środowiska CLR z zadaniami za pośrednictwem hosta zamiast korzystania ze standardowego wątku lub funkcji światłowodowych systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2768f-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="2768f-207">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-207">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="2768f-208">Zapewnia metody dla środowiska CLR w celu skonfigurowania puli wątków i umieszczania w kolejce elementów roboczych w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="2768f-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="2768f-209">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-209">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="2768f-210">Zapewnia metody kontrolowania obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2768f-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="2768f-211">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="2768f-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="2768f-212">Zapewnia metodę odpakowania obiektów marshal-by-Value z operatora pośredni.</span><span class="sxs-lookup"><span data-stu-id="2768f-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="2768f-213">ITypeName, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-213">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="2768f-214">Zapewnia metody uzyskiwania informacji o nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="2768f-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="2768f-215">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="2768f-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="2768f-216">ITypeNameBuilder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-216">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="2768f-217">Zapewnia metody tworzenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="2768f-217">Provides methods for building a type name.</span></span> <span data-ttu-id="2768f-218">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="2768f-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="2768f-219">ITypeNameFactory, interfejs</span><span class="sxs-lookup"><span data-stu-id="2768f-219">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="2768f-220">Dostarcza metody służące do dekonstrukcji nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="2768f-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="2768f-221">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="2768f-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="2768f-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="2768f-222">"IValidator"</span></span>  
 <span data-ttu-id="2768f-223">Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="2768f-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2768f-224">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2768f-224">Related Sections</span></span>  
 [<span data-ttu-id="2768f-225">Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2768f-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="2768f-226">Zawiera tematy opisujące Interfejsy hostingu dostępne w .NET Framework w wersji 1,0 i 1,1.</span><span class="sxs-lookup"><span data-stu-id="2768f-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="2768f-227">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="2768f-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="2768f-228">Zawiera tematy opisujące Interfejsy hostingu dostępne w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2768f-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
