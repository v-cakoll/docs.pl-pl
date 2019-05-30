---
title: Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6405c61429d56b125fd0327824482bf702e41319
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380278"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="aed65-102">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="aed65-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="aed65-103">W tej sekcji opisano niezarządzane interfejsy hostów można użyć do integracji środowisko uruchomieniowe języka wspólnego (CLR) w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], .NET Framework 4.5 i nowsze wersje w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="aed65-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="aed65-104">Te interfejsy dostarczać metody do hosta skonfigurować i załadowania środowiska uruchomieniowego do procesu.</span><span class="sxs-lookup"><span data-stu-id="aed65-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="aed65-105">Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], hostingu wszystkie interfejsy mają następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="aed65-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="aed65-106">Używają Zarządzanie okresem istnienia (`AddRef` i `Release`), hermetyzacji (niejawne context) i `QueryInterface` z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="aed65-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="aed65-107">Istnieje nie należy używać typów modelu COM takich jak `BSTR`, `SAFEARRAY`, lub `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="aed65-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="aed65-108">Nie ma żadnych modeli typu apartment, agregacji ani rejestru aktywacji używanego przez [funkcja CoCreateInstance](https://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="aed65-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](https://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aed65-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="aed65-109">In This Section</span></span>  
 [<span data-ttu-id="aed65-110">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="aed65-111">Udostępnia metody, które Sprawdź domenę aplikacji pamięci i Procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="aed65-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="aed65-112">ICLRDomainManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="aed65-113">Umożliwia hosta określić Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji i określić właściwości inicjowania.</span><span class="sxs-lookup"><span data-stu-id="aed65-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="aed65-114">ICLRGCManager2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="aed65-115">Udostępnia [setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metody, która umożliwia hosta można skonfigurować rozmiaru segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0 na wartości większej niż `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="aed65-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="aed65-116">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="aed65-117">Zawiera metody, które zwracają określonej wersji środowiska CLR, listę wszystkich zainstalowanych CLRs, listy wszystkie środowiska uruchomieniowe w trakcie, zwracają interfejs aktywacji i odnajdź wersję środowiska CLR używana do kompilowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="aed65-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="aed65-118">ICLRMetaHostPolicy, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="aed65-119">Udostępnia [getrequestedruntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodę, która udostępnia interfejs CLR na podstawie kryteriów zasad, zestaw zarządzany, wersji i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aed65-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="aed65-120">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="aed65-121">Udostępnia metody, które zwracają informacje dotyczące określonego środowiska uruchomieniowego, w tym wersja, katalog i stan obciążenia.</span><span class="sxs-lookup"><span data-stu-id="aed65-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="aed65-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="aed65-123">Zawiera podstawowe statyczne funkcje globalne do podpisywania zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="aed65-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="aed65-124">Wszystkie [iclrstrongname —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) metody zwracają standardowa COM wartości HRESULT.</span><span class="sxs-lookup"><span data-stu-id="aed65-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="aed65-125">ICLRStrongName2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="aed65-126">Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).</span><span class="sxs-lookup"><span data-stu-id="aed65-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="aed65-127">ICLRTask2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed65-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="aed65-128">Oferuje wszystkie funkcje [iclrtask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); ponadto udostępnia metody, które umożliwiają wątku przerywa opóźnionych w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="aed65-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aed65-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="aed65-129">Related Sections</span></span>  
 [<span data-ttu-id="aed65-130">Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="aed65-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="aed65-131">W tym artykule opisano interfejsami hostingu, wyposażone w wersjach programu .NET Framework 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="aed65-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="aed65-132">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="aed65-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="aed65-133">W tym artykule opisano interfejsami hostingu, wyposażone w .NET Framework w wersji 2.0, 3.0 i 3.5.</span><span class="sxs-lookup"><span data-stu-id="aed65-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="aed65-134">Hosting</span><span class="sxs-lookup"><span data-stu-id="aed65-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="aed65-135">Wprowadza hosting w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed65-135">Introduces hosting in the .NET Framework.</span></span>
