---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46e468f10c1c07425f7ecb3589bd114d12180554
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502596"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="6f8c3-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime — Metoda</span><span class="sxs-lookup"><span data-stu-id="6f8c3-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="6f8c3-103">Pobiera całkowitego czasu procesora użytą przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, od momentu utworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f8c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f8c3-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f8c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f8c3-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="6f8c3-106">[in] Identyfikator domeny żądanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="6f8c3-107">[out] Wskaźnik do całkowitego czasu procesora użytą przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, od momentu utworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="6f8c3-108">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f8c3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6f8c3-109">Return Value</span></span>  
  
|<span data-ttu-id="6f8c3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f8c3-110">HRESULT</span></span>|<span data-ttu-id="6f8c3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6f8c3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f8c3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f8c3-112">S_OK</span></span>|<span data-ttu-id="6f8c3-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="6f8c3-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="6f8c3-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="6f8c3-115">Domeny aplikacji został zwolniony lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="6f8c3-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f8c3-116">E_FAIL</span></span>|<span data-ttu-id="6f8c3-117">Monitorowanie zasobów domeny aplikacji nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="6f8c3-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="6f8c3-118">-or-</span></span><br /><br /> <span data-ttu-id="6f8c3-119">Wszystkie inne błędy.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f8c3-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f8c3-120">Remarks</span></span>  
 <span data-ttu-id="6f8c3-121">Ta metoda jest odpowiednikiem niezarządzanych zarządzaną <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f8c3-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f8c3-122">Requirements</span></span>  
 <span data-ttu-id="6f8c3-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f8c3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f8c3-124">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6f8c3-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6f8c3-125">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f8c3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f8c3-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f8c3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f8c3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f8c3-127">See also</span></span>
- [<span data-ttu-id="6f8c3-128">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f8c3-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="6f8c3-129">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6f8c3-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6f8c3-130">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="6f8c3-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="6f8c3-131">Hosting</span><span class="sxs-lookup"><span data-stu-id="6f8c3-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
