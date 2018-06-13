---
title: Interfejsy hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435644"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="ec7d8-102">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="ec7d8-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="ec7d8-103">W tej sekcji opisano interfejsów, które niezarządzanych hostów można użyć do integracji środowisko uruchomieniowe języka wspólnego (CLR) w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="ec7d8-104">Informacje odnoszą się do platformy .NET Framework w wersji 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="ec7d8-105">Te interfejsy Włącz hosta do kontrolowania wielu aspektów więcej czasu wykonywania niż w wersji 1.0, 1.1 i podaj znacznie większego integrację środowiska CLR i model wykonania hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="ec7d8-106">W programie .NET Framework w wersji 1.0, 1.1 obsługi włączone niezarządzane hosta można załadować środowiska CLR do procesu, konfigurowanie niektórych ustawień i otrzymywanie powiadomień o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="ec7d8-107">Jednak ogólnie rzecz biorąc, hosta i środowiska CLR został uruchomiony niezależnie w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="ec7d8-108">.NET Framework w wersji 2.0 i nowszych wersji nowe warstwy abstrakcji umożliwiają hosta zapewniają wiele zasobów oferowanych przez typów w zestawie Win32 i rozszerzyć zestaw funkcji, które można skonfigurować hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec7d8-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ec7d8-109">In This Section</span></span>  
 [<span data-ttu-id="ec7d8-110">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="ec7d8-111">Udostępnia metody, która wykonuje wywołanie zwrotne zarejestrowane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="ec7d8-112">IApartmentCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="ec7d8-113">Udostępnia metody do tworzenia wywołań zwrotnych w apartamencie.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="ec7d8-114">IAppDomainBinding, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="ec7d8-115">Udostępnia metody dla konfiguracji środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="ec7d8-116">ICatalogServices, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="ec7d8-117">Udostępnia metody dla skatalogowania usług.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="ec7d8-118">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="ec7d8-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="ec7d8-119">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="ec7d8-120">Udostępnia metody, które obsługują komunikację między hostem i informacje o zestawach środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="ec7d8-121">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="ec7d8-122">Zarządza listę zestawów, które są ładowane przez środowisko CLR, a nie przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="ec7d8-123">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="ec7d8-124">Udostępnia metody dla hosta w celu uzyskania dostępu do i skonfigurować różne aspekty środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="ec7d8-125">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="ec7d8-126">Udostępnia metody umożliwiające hosta do skojarzenia z identyfikatorem i przyjazną nazwę zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="ec7d8-127">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="ec7d8-128">Udostępnia metody, które umożliwiają hosta skonfigurować zrzuty stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="ec7d8-129">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="ec7d8-130">Udostępnia metody umożliwiające hosta do interakcji z system CLR czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="ec7d8-131">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="ec7d8-132">Udostępnia metody dla hosta ocenić i komunikować się zmiany informacji o zasadach dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="ec7d8-133">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="ec7d8-134">Umożliwia hosta blokowanie określonych klas zarządzanych, metody, właściwości i pola w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="ec7d8-135">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="ec7d8-136">Implementuje metody wywołania zwrotnego, która umożliwia hosta powiadomiono CLR stan określonego żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="ec7d8-137">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="ec7d8-138">Włącza hosta do warunków braku pamięci raportu w sposób podobny do środowiska Win32 `CreateMemoryResourceNotification` funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="ec7d8-139">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="ec7d8-140">Udostępnia metody umożliwiające hosta umożliwia rejestrowanie i wyrejestrowywanie wywołań zwrotnych dla zdarzenia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="ec7d8-141">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="ec7d8-142">Udostępnia metody, które umożliwiają hosta określić zasady akcje do wykonania w przypadku awarii i przekroczeń limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="ec7d8-143">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="ec7d8-144">Udostępnia metody umożliwiające hosta można uzyskać za pomocą zestawu tożsamości informacje, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia i zrozumienie tej tożsamości sondowania tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="ec7d8-145">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="ec7d8-146">Udostępnia metody, które umożliwiają hosta do manipulowania zbiór zestawów odwołuje się do pliku lub strumienia za pomocą zestawu danych tożsamości, które jest wewnętrzna CLR, bez konieczności tworzenia i zrozumienie tych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="ec7d8-147">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="ec7d8-148">Zapewnia funkcje podobne do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), z dodatkową metodę można ustawić interfejsu kontroli hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="ec7d8-149">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="ec7d8-150">Udostępnia metody dla hosta, aby uzyskać informacje dotyczące zadań i wykrył zakleszczenie w jej wykonanie synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="ec7d8-151">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="ec7d8-152">Udostępnia metody umożliwiające hosta do wysyłania żądań CLR lub w celu udostępnienia powiadomień do środowiska CLR o skojarzonego zadania.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="ec7d8-153">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="ec7d8-154">Udostępnia metody umożliwiające hosta do żądania jawnie, czy CLR utworzyć nowe zadanie, Pobierz aktualnie wykonywanego zadania i ustaw geograficzne języka i kultury dla zadania.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="ec7d8-155">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="ec7d8-156">Udostępnia metody dla sprawdzanie poprawności przenośne obrazy wykonywalne (PE) i raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="ec7d8-157">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="ec7d8-158">Udostępnia metody do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="ec7d8-159">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="ec7d8-160">Udostępnia metody, aby uzyskać dostęp do puli wątków.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="ec7d8-161">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="ec7d8-162">Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="ec7d8-163">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="ec7d8-164">Udostępnia metody dla powiadamiania hosta o blokowania i odblokowywania wątków przez usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="ec7d8-165">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="ec7d8-166">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="ec7d8-167">IGCHost2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="ec7d8-168">Udostępnia [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodę, która umożliwia hosta ustawioną rozmiar segmentu kolekcji pamięci i maksymalny rozmiar generowania systemu czyszczenia pamięci zerowej wartości większej niż `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="ec7d8-169">IGCHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="ec7d8-170">Udostępnia metody, która włącza moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="ec7d8-171">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="ec7d8-172">Udostępnia metody do uczestnictwa w planowaniu wątków, które można zablokować dla wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="ec7d8-173">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="ec7d8-174">Udostępnia metody, które umożliwiają hosta określić zestawy zestawy, które powinny być załadowane przez środowisko CLR lub przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="ec7d8-175">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="ec7d8-176">Udostępnia metody umożliwiające hosta można załadować zestawów i modułów, niezależnie od środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="ec7d8-177">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="ec7d8-178">Udostępnia reprezentację automatyczne resetowanie zdarzenia implementowanego przez zdarzenie hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="ec7d8-179">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="ec7d8-180">Udostępnia metody konfigurowania ładowania zestawów i określania, które hosting interfejsy obsługuje hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="ec7d8-181">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="ec7d8-182">Służy jako hosta reprezentację sekcja krytyczna dla wątków.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="ec7d8-183">IHostGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="ec7d8-184">Udostępnia metody, które powiadamiają o hoście zdarzenia mechanizmu kolekcji garbage zaimplementowana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="ec7d8-185">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="ec7d8-186">Udostępnia metody umożliwiające CLR wchodzić w interakcje z portów We/Wy dostarczone przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="ec7d8-187">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="ec7d8-188">Udostępnia metody dla środowiska CLR do żądania szczegółowych alokacji sterty za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="ec7d8-189">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="ec7d8-190">Udostępnia implementację hosta reprezentację zdarzeń resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="ec7d8-191">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="ec7d8-192">Udostępnia metody dla środowiska CLR na wysyłanie żądań pamięci wirtualnej za pośrednictwem hosta, a nie przy użyciu standardowych funkcji Win32 w pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="ec7d8-193">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="ec7d8-194">Udostępnia metody, które powiadamiają o hoście akcje, które wykonuje CLR w przypadku liczby przerywa przekroczenia limitu czasu lub błędów.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="ec7d8-195">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="ec7d8-196">Umożliwia CLR zachować informacje kontekstu zabezpieczeń zaimplementowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="ec7d8-197">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="ec7d8-198">Udostępnia metody umożliwiające dostęp do i kontrolę nad wątku aktualnie wykonywane w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="ec7d8-199">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="ec7d8-200">Udostępnia reprezentację semafora zaimplementowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="ec7d8-201">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="ec7d8-202">Udostępnia metody dla CLR można utworzyć w nim elementów podstawowych synchronizacji przez wywołanie przez hosta, zamiast używać funkcji synchronizacji Win32.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="ec7d8-203">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="ec7d8-204">Udostępnia metody umożliwiające CLR do komunikowania się z hosta do zarządzania zadaniami.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="ec7d8-205">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="ec7d8-206">Udostępnia metody umożliwiające CLR do pracy z zadaniami za pośrednictwem hosta zamiast przy użyciu funkcji wątki lub włókna standardowy system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="ec7d8-207">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="ec7d8-208">Udostępnia metody dla środowiska CLR do skonfigurowania puli wątków i do kolejki elementów roboczych w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="ec7d8-209">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="ec7d8-210">Udostępnia metody umożliwiające sterowanie zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="ec7d8-211">"IObjectHandle"</span><span class="sxs-lookup"><span data-stu-id="ec7d8-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="ec7d8-212">Zapewnia metodę otwierania obiektów kierowanie przez wartości z pośrednie.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="ec7d8-213">ITypeName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="ec7d8-214">Udostępnia metody uzyskiwania informacji na nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="ec7d8-215">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="ec7d8-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="ec7d8-216">ITypeNameBuilder, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="ec7d8-217">Udostępnia metody do tworzenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-217">Provides methods for building a type name.</span></span> <span data-ttu-id="ec7d8-218">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="ec7d8-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="ec7d8-219">ITypeNameFactory, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec7d8-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="ec7d8-220">Udostępnia metody dla deconstructing nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="ec7d8-221">(Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="ec7d8-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="ec7d8-222">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="ec7d8-222">"IValidator"</span></span>  
 <span data-ttu-id="ec7d8-223">Udostępnia metody dla sprawdzanie poprawności przenośne obrazy wykonywalne (PE) i raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec7d8-224">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ec7d8-224">Related Sections</span></span>  
 [<span data-ttu-id="ec7d8-225">Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="ec7d8-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="ec7d8-226">Zawiera tematy, które opisują interfejsy hostingu dostępne w programie .NET Framework w wersji 1.0, 1.1.</span><span class="sxs-lookup"><span data-stu-id="ec7d8-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="ec7d8-227">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="ec7d8-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="ec7d8-228">Zawiera tematy, które opisują interfejsy hostingu w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec7d8-228">Contains topics that describe the hosting interfaces provided in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>
