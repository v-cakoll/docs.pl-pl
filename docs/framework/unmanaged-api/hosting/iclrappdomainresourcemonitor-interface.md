---
title: ICLRAppDomainResourceMonitor — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc2326c72c9a1c63c4740608e120ace5dc83ebee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434873"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="cd5b2-102">ICLRAppDomainResourceMonitor — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd5b2-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="cd5b2-103">Udostępnia metody, które sprawdzić pamięci i Procesora CPU domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd5b2-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd5b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cd5b2-104">Methods</span></span>  
  
|<span data-ttu-id="cd5b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd5b2-105">Method</span></span>|<span data-ttu-id="cd5b2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cd5b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd5b2-107">GetCurrentAllocated, metoda</span><span class="sxs-lookup"><span data-stu-id="cd5b2-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="cd5b2-108">Pobiera całkowity rozmiar w bajtach, wszystkie wprowadzone przez domenę aplikacji od czasu utworzenia, bez odjęcie ilości pamięci, które zostały zebrane pamięci alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd5b2-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="cd5b2-109">GetCurrentSurvived, metoda</span><span class="sxs-lookup"><span data-stu-id="cd5b2-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="cd5b2-110">Pobiera liczbę bajtów, który udało się przetrwać ostatniego pełnego, blokowanie odzyskiwania pamięci i który odwołuje się bieżącej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd5b2-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="cd5b2-111">GetCurrentCpuTime, metoda</span><span class="sxs-lookup"><span data-stu-id="cd5b2-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="cd5b2-112">Pobiera całkowitego czasu procesora użytą przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, ponieważ domena aplikacji została utworzona.</span><span class="sxs-lookup"><span data-stu-id="cd5b2-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd5b2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd5b2-113">Remarks</span></span>  
 <span data-ttu-id="cd5b2-114">`ICLRAppDomainResourceMonitor` Interfejs zapewnia funkcje podobne do następujących właściwości zarządzane:</span><span class="sxs-lookup"><span data-stu-id="cd5b2-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="cd5b2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd5b2-115">Requirements</span></span>  
 <span data-ttu-id="cd5b2-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd5b2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd5b2-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cd5b2-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cd5b2-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd5b2-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd5b2-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd5b2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd5b2-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd5b2-120">See Also</span></span>  
 [<span data-ttu-id="cd5b2-121">\<appdomainresourcemonitoring — > — Element</span><span class="sxs-lookup"><span data-stu-id="cd5b2-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [<span data-ttu-id="cd5b2-122">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="cd5b2-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="cd5b2-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cd5b2-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="cd5b2-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="cd5b2-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
