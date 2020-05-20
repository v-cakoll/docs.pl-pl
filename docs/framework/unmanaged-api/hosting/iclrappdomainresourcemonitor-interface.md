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
ms.openlocfilehash: 08dc0f0891d960cb7b402b30455e606aaff7bcea
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616011"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="8646e-102">ICLRAppDomainResourceMonitor — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8646e-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="8646e-103">Dostarcza metody, które sprawdzają użycie procesora i pamięci domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8646e-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8646e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8646e-104">Methods</span></span>  
  
|<span data-ttu-id="8646e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8646e-105">Method</span></span>|<span data-ttu-id="8646e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8646e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8646e-107">GetCurrentAllocated, metoda</span><span class="sxs-lookup"><span data-stu-id="8646e-107">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="8646e-108">Pobiera łączny rozmiar (w bajtach) wszystkich alokacji pamięci wykonanych przez domenę aplikacji od momentu utworzenia, bez odejmowania pamięci, która została zebrana jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="8646e-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="8646e-109">GetCurrentSurvived, metoda</span><span class="sxs-lookup"><span data-stu-id="8646e-109">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="8646e-110">Pobiera liczbę bajtów, które przeżyły ostatnią pełną, blokującą wyrzucanie elementów bezużytecznych i przywoływanych przez bieżącą domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8646e-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="8646e-111">GetCurrentCpuTime, metoda</span><span class="sxs-lookup"><span data-stu-id="8646e-111">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="8646e-112">Pobiera łączny czas procesora, który był używany przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, od momentu utworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8646e-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8646e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8646e-113">Remarks</span></span>  
 <span data-ttu-id="8646e-114">`ICLRAppDomainResourceMonitor`Interfejs udostępnia funkcje podobne do następujących właściwości zarządzanych:</span><span class="sxs-lookup"><span data-stu-id="8646e-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="8646e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8646e-115">Requirements</span></span>  
 <span data-ttu-id="8646e-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8646e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8646e-117">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="8646e-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8646e-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8646e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8646e-119">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8646e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8646e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8646e-120">See also</span></span>

- [<span data-ttu-id="8646e-121">\<appDomainResourceMonitoring, element></span><span class="sxs-lookup"><span data-stu-id="8646e-121">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="8646e-122">Monitorowanie zasobów domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8646e-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="8646e-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8646e-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="8646e-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="8646e-124">Hosting</span></span>](index.md)
