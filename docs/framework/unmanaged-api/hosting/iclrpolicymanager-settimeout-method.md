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
ms.openlocfilehash: 5b5a389af718322d1e0fffebae046bf28731877b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435780"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="25d5c-102">ICLRPolicyManager::SetTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="25d5c-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="25d5c-103">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="25d5c-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25d5c-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25d5c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25d5c-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="25d5c-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący, wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) do których chcesz ustawić limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="25d5c-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="25d5c-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="25d5c-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="25d5c-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="25d5c-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="25d5c-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="25d5c-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="25d5c-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="25d5c-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="25d5c-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="25d5c-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="25d5c-112">[in] Nowa wartość limitu czasu, w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="25d5c-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="25d5c-113">Wartość INFINITE powoduje, że nigdy nie upłynął limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="25d5c-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25d5c-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="25d5c-114">Return Value</span></span>  
  
|<span data-ttu-id="25d5c-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25d5c-115">HRESULT</span></span>|<span data-ttu-id="25d5c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="25d5c-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25d5c-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="25d5c-117">S_OK</span></span>|<span data-ttu-id="25d5c-118">`SetTimeout` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="25d5c-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="25d5c-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25d5c-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25d5c-120">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="25d5c-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25d5c-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25d5c-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25d5c-122">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="25d5c-122">The call timed out.</span></span>|  
|<span data-ttu-id="25d5c-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25d5c-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25d5c-124">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="25d5c-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25d5c-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25d5c-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25d5c-126">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="25d5c-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25d5c-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25d5c-127">E_FAIL</span></span>|<span data-ttu-id="25d5c-128">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="25d5c-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25d5c-129">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="25d5c-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25d5c-130">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="25d5c-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="25d5c-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="25d5c-131">E_INVALIDARG</span></span>|<span data-ttu-id="25d5c-132">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="25d5c-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25d5c-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25d5c-133">Requirements</span></span>  
 <span data-ttu-id="25d5c-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25d5c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25d5c-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25d5c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25d5c-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25d5c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25d5c-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25d5c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d5c-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25d5c-138">See Also</span></span>  
 [<span data-ttu-id="25d5c-139">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="25d5c-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="25d5c-140">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="25d5c-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="25d5c-141">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="25d5c-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
