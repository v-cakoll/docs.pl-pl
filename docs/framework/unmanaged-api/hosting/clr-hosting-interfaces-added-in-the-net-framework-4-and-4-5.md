---
title: Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 8484b47549f83795778420048d610e2d1626d87b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899716"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="dd736-102">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="dd736-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="dd736-103">W tej sekcji opisano interfejsy, które mogą być używane przez niezarządzane hosty do integrowania środowiska uruchomieniowego języka wspólnego (CLR) w .NET Framework 4, .NET Framework 4,5 i nowszych wersjach w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="dd736-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="dd736-104">Te interfejsy zapewniają metody hosta do konfigurowania i ładowania środowiska uruchomieniowego do procesu.</span><span class="sxs-lookup"><span data-stu-id="dd736-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="dd736-105">Począwszy od .NET Framework 4, wszystkie interfejsy hostingu mają następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="dd736-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="dd736-106">Wykorzystują one zarządzanie okresem istnienia (`AddRef` i `Release`), hermetyzację (niejawny kontekst) i `QueryInterface` z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd736-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="dd736-107">Nie używają one typów COM, takich jak `BSTR`, `SAFEARRAY`lub `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="dd736-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="dd736-108">Nie istnieją modele komórek, agregacja ani aktywacja rejestru, które używają [funkcji CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span><span class="sxs-lookup"><span data-stu-id="dd736-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd736-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dd736-109">In This Section</span></span>  
 [<span data-ttu-id="dd736-110">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="dd736-111">Dostarcza metody, które sprawdzają użycie procesora i pamięci domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd736-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="dd736-112">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="dd736-113">Umożliwia hostowi określenie Menedżera domeny aplikacji, który będzie używany do inicjowania domyślnej domeny aplikacji, oraz do określania właściwości inicjacji.</span><span class="sxs-lookup"><span data-stu-id="dd736-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="dd736-114">ICLRGCManager2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="dd736-115">Udostępnia metodę [SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) , która umożliwia hostowi Ustawianie rozmiaru segmentu wyrzucania elementów bezużytecznych i maksymalnego rozmiaru generacji 0 systemu wyrzucania elementów bezużytecznych do wartości większej niż `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="dd736-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="dd736-116">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="dd736-117">Dostarcza metody, które zwracają określoną wersję środowiska CLR, wyświetla listę wszystkich zainstalowanych CLRs, wyświetla wszystkie środowiska uruchomieniowe w procesie, zwracają interfejs aktywacji i odnajdują wersję środowiska CLR używaną do kompilowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="dd736-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="dd736-118">ICLRMetaHostPolicy, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="dd736-119">Udostępnia metodę [GetRequestedRuntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , która dostarcza interfejs CLR na podstawie kryteriów zasad, zestawu zarządzanego, wersji i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dd736-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="dd736-120">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="dd736-121">Dostarcza metody, które zwracają informacje dotyczące określonego środowiska uruchomieniowego, w tym wersję, katalog i stan ładowania.</span><span class="sxs-lookup"><span data-stu-id="dd736-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="dd736-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="dd736-123">Udostępnia podstawowe globalne funkcje statyczne do podpisywania zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="dd736-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="dd736-124">Wszystkie metody [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) zwracają standardowe wartości HRESULT modelu com.</span><span class="sxs-lookup"><span data-stu-id="dd736-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="dd736-125">ICLRStrongName2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="dd736-126">Zapewnia możliwość tworzenia silnych nazw przy użyciu grupy SHA-2 bezpiecznych algorytmów wyznaczania wartości skrótu (SHA-256, SHA-384 i SHA-512).</span><span class="sxs-lookup"><span data-stu-id="dd736-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="dd736-127">ICLRTask2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd736-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="dd736-128">Oferuje wszystkie funkcje [interfejsu ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Ponadto udostępnia metody zezwalające na opóźnione przerywanie wątków w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="dd736-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd736-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="dd736-129">Related Sections</span></span>  
 [<span data-ttu-id="dd736-130">Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dd736-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="dd736-131">Opisuje interfejsy hostingu udostępniane w .NET Framework wersje 1,0 i 1,1.</span><span class="sxs-lookup"><span data-stu-id="dd736-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="dd736-132">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dd736-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="dd736-133">Opisuje interfejsy hostingu udostępniane w .NET Framework wersje 2,0, 3,0 i 3,5.</span><span class="sxs-lookup"><span data-stu-id="dd736-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="dd736-134">Hosting</span><span class="sxs-lookup"><span data-stu-id="dd736-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="dd736-135">Wprowadza hosting w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd736-135">Introduces hosting in the .NET Framework.</span></span>
