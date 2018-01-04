---
title: "ICLRAppDomainResourceMonitor::GetCurrentAllocated — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2b69f2f8e8273c07d277ff7460ad977fade89ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="f911e-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated — Metoda</span><span class="sxs-lookup"><span data-stu-id="f911e-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="f911e-103">Pobiera całkowity rozmiar w bajtach, wszystkie wprowadzone przez domenę aplikacji od czasu utworzenia, bez odjęcie ilości pamięci, które zostały zebrane pamięci alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="f911e-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f911e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f911e-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f911e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f911e-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="f911e-106">[in] Identyfikator domeny żądanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f911e-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="f911e-107">[out] Wskaźnik całkowity rozmiar wszystkich alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="f911e-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f911e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f911e-108">Return Value</span></span>  
 <span data-ttu-id="f911e-109">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="f911e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f911e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f911e-110">HRESULT</span></span>|<span data-ttu-id="f911e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f911e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f911e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f911e-112">S_OK</span></span>|<span data-ttu-id="f911e-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f911e-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f911e-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="f911e-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="f911e-115">Domeny aplikacji został zwolniony lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f911e-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f911e-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f911e-116">Remarks</span></span>  
 <span data-ttu-id="f911e-117">Ta metoda jest odpowiednikiem niezarządzane zarządzanej <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f911e-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f911e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f911e-118">Requirements</span></span>  
 <span data-ttu-id="f911e-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f911e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f911e-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f911e-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f911e-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f911e-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f911e-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f911e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f911e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f911e-123">See Also</span></span>  
 [<span data-ttu-id="f911e-124">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="f911e-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="f911e-125">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="f911e-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="f911e-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f911e-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f911e-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="f911e-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
