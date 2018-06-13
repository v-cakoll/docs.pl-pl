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
ms.openlocfilehash: 4011881e98c109458bf87efcc1b09463c064f23f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431958"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="ff700-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff700-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="ff700-103">Pobiera całkowity rozmiar w bajtach, wszystkie wprowadzone przez domenę aplikacji od czasu utworzenia, bez odjęcie ilości pamięci, które zostały zebrane pamięci alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="ff700-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff700-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff700-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff700-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff700-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="ff700-106">[in] Identyfikator domeny żądanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff700-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="ff700-107">[out] Wskaźnik całkowity rozmiar wszystkich alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="ff700-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff700-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ff700-108">Return Value</span></span>  
 <span data-ttu-id="ff700-109">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="ff700-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ff700-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff700-110">HRESULT</span></span>|<span data-ttu-id="ff700-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ff700-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff700-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff700-112">S_OK</span></span>|<span data-ttu-id="ff700-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ff700-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="ff700-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="ff700-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="ff700-115">Domeny aplikacji został zwolniony lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ff700-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff700-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff700-116">Remarks</span></span>  
 <span data-ttu-id="ff700-117">Ta metoda jest odpowiednikiem niezarządzane zarządzanej <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff700-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff700-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff700-118">Requirements</span></span>  
 <span data-ttu-id="ff700-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff700-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff700-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ff700-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ff700-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff700-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff700-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff700-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff700-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff700-123">See Also</span></span>  
 [<span data-ttu-id="ff700-124">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="ff700-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="ff700-125">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ff700-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="ff700-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ff700-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="ff700-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="ff700-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
