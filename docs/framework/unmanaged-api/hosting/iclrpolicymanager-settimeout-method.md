---
title: "ICLRPolicyManager::SetTimeout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31dfd4654f849d01958be2690afed0f31c736dfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="b41d0-102">ICLRPolicyManager::SetTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="b41d0-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="b41d0-103">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="b41d0-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b41d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b41d0-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b41d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b41d0-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="b41d0-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący, wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) do których chcesz ustawić limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="b41d0-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="b41d0-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="b41d0-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="b41d0-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="b41d0-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="b41d0-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="b41d0-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="b41d0-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="b41d0-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="b41d0-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="b41d0-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="b41d0-112">[in] Nowa wartość limitu czasu, w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="b41d0-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="b41d0-113">Wartość INFINITE powoduje, że nigdy nie upłynął limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="b41d0-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b41d0-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b41d0-114">Return Value</span></span>  
  
|<span data-ttu-id="b41d0-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b41d0-115">HRESULT</span></span>|<span data-ttu-id="b41d0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b41d0-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b41d0-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="b41d0-117">S_OK</span></span>|<span data-ttu-id="b41d0-118">`SetTimeout`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b41d0-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="b41d0-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b41d0-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b41d0-120">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b41d0-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b41d0-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b41d0-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b41d0-122">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b41d0-122">The call timed out.</span></span>|  
|<span data-ttu-id="b41d0-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b41d0-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b41d0-124">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b41d0-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b41d0-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b41d0-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b41d0-126">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b41d0-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b41d0-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b41d0-127">E_FAIL</span></span>|<span data-ttu-id="b41d0-128">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b41d0-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b41d0-129">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b41d0-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b41d0-130">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b41d0-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b41d0-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b41d0-131">E_INVALIDARG</span></span>|<span data-ttu-id="b41d0-132">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="b41d0-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b41d0-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b41d0-133">Requirements</span></span>  
 <span data-ttu-id="b41d0-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b41d0-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b41d0-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b41d0-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b41d0-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b41d0-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b41d0-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b41d0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41d0-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b41d0-138">See Also</span></span>  
 [<span data-ttu-id="b41d0-139">EClrOperation — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b41d0-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="b41d0-140">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="b41d0-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b41d0-141">ICLRPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="b41d0-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
