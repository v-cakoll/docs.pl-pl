---
title: ICLRPolicyManager::SetTimeout — Metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b16cc6a899b1ad5c814c29a93c6125250ca8186d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133578"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="ca743-102">ICLRPolicyManager::SetTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca743-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="ca743-103">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="ca743-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca743-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca743-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca743-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca743-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="ca743-106">[in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazując typowych operacji środowiska uruchomieniowego (języka wspólnego CLR) języka, dla którego ma zostać ustawiony limit czasu.</span><span class="sxs-lookup"><span data-stu-id="ca743-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="ca743-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="ca743-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="ca743-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="ca743-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="ca743-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="ca743-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="ca743-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="ca743-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="ca743-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="ca743-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="ca743-112">[in] Nowa wartość limitu czasu, w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="ca743-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="ca743-113">Wartość INFINITE powoduje, że operacja nigdy nie przekroczy limit czasu.</span><span class="sxs-lookup"><span data-stu-id="ca743-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca743-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ca743-114">Return Value</span></span>  
  
|<span data-ttu-id="ca743-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca743-115">HRESULT</span></span>|<span data-ttu-id="ca743-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ca743-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca743-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca743-117">S_OK</span></span>|<span data-ttu-id="ca743-118">`SetTimeout` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="ca743-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="ca743-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca743-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca743-120">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ca743-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca743-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca743-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca743-122">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ca743-122">The call timed out.</span></span>|  
|<span data-ttu-id="ca743-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca743-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca743-124">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ca743-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca743-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca743-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca743-126">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ca743-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca743-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca743-127">E_FAIL</span></span>|<span data-ttu-id="ca743-128">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ca743-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca743-129">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ca743-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca743-130">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca743-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ca743-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ca743-131">E_INVALIDARG</span></span>|<span data-ttu-id="ca743-132">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="ca743-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca743-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca743-133">Requirements</span></span>  
 <span data-ttu-id="ca743-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca743-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca743-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca743-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca743-136">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca743-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca743-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca743-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca743-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca743-138">See also</span></span>

- [<span data-ttu-id="ca743-139">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ca743-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="ca743-140">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca743-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ca743-141">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca743-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
