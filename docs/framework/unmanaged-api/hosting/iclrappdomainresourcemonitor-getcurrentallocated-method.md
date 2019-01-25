---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43d3234a6bd579238068dba9b37ff48a758f6ed3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693791"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="1f8b1-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f8b1-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="1f8b1-103">Pobiera całkowity rozmiar w bajtach, wszystkie alokacje pamięci, które zostały wprowadzone przez domenę aplikacji, ponieważ został utworzony, bez odjęcie ilości pamięci, która została zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1f8b1-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f8b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f8b1-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f8b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f8b1-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="1f8b1-106">[in] Identyfikator domeny żądanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f8b1-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="1f8b1-107">[out] Wskaźnik to łączny rozmiar wszystkich alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="1f8b1-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f8b1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f8b1-108">Return Value</span></span>  
 <span data-ttu-id="1f8b1-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="1f8b1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1f8b1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f8b1-110">HRESULT</span></span>|<span data-ttu-id="1f8b1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1f8b1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f8b1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f8b1-112">S_OK</span></span>|<span data-ttu-id="1f8b1-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1f8b1-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="1f8b1-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="1f8b1-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="1f8b1-115">Domeny aplikacji został zwolniony lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="1f8b1-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f8b1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f8b1-116">Remarks</span></span>  
 <span data-ttu-id="1f8b1-117">Ta metoda jest odpowiednikiem niezarządzanych zarządzaną <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1f8b1-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f8b1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f8b1-118">Requirements</span></span>  
 <span data-ttu-id="1f8b1-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f8b1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f8b1-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1f8b1-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1f8b1-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f8b1-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f8b1-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f8b1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f8b1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f8b1-123">See also</span></span>
- [<span data-ttu-id="1f8b1-124">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f8b1-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="1f8b1-125">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="1f8b1-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="1f8b1-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1f8b1-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1f8b1-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="1f8b1-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
