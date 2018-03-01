---
title: "IHostControl::SetAppDomainManager — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d689a664f5bad19a70a8d635beb1f25f33da6ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="724cf-102">IHostControl::SetAppDomainManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="724cf-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="724cf-103">Powiadamia hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="724cf-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="724cf-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="724cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="724cf-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="724cf-106">[in] Identyfikator numeryczny wybranego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="724cf-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="724cf-107">[in] Wskaźnik do <xref:System.AppDomainManager> obiektu implementującego hosta jako `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="724cf-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="724cf-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="724cf-108">Return Value</span></span>  
  
|<span data-ttu-id="724cf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="724cf-109">HRESULT</span></span>|<span data-ttu-id="724cf-110">Opis</span><span class="sxs-lookup"><span data-stu-id="724cf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="724cf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="724cf-111">S_OK</span></span>|<span data-ttu-id="724cf-112">`SetAppDomainManager`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="724cf-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="724cf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="724cf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="724cf-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="724cf-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="724cf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="724cf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="724cf-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="724cf-116">The call timed out.</span></span>|  
|<span data-ttu-id="724cf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="724cf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="724cf-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="724cf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="724cf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="724cf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="724cf-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="724cf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="724cf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="724cf-121">E_FAIL</span></span>|<span data-ttu-id="724cf-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="724cf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="724cf-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="724cf-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="724cf-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="724cf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="724cf-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="724cf-125">Remarks</span></span>  
 <span data-ttu-id="724cf-126"><xref:System.AppDomainManager> Udostępnia mechanizm do ładowania początkowego kodu zarządzanego i sterowania tworzenie i ustawienia każdego hosta <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="724cf-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="724cf-127"><xref:System.AppDomainManager> Jest ładowany do każdego <xref:System.AppDomain> podczas którego <xref:System.AppDomain> jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="724cf-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="724cf-128">Jeśli wybiera, CLR informuje hosta, czy domena aplikacji została utworzona przez ustawienie wartości `pUnkAppDomainManager` parametru.</span><span class="sxs-lookup"><span data-stu-id="724cf-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="724cf-129">Jego wykonywania `SetAppDomainManager` metody hosta można ustawić nazwy zestawu i typu Menedżer domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="724cf-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="724cf-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="724cf-130">Requirements</span></span>  
 <span data-ttu-id="724cf-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="724cf-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="724cf-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="724cf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="724cf-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="724cf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="724cf-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="724cf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724cf-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="724cf-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="724cf-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="724cf-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
