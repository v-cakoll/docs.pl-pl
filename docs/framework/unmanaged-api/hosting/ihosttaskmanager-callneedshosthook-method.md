---
title: "IHostTaskManager::CallNeedsHostHook — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.CallNeedsHostHook
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0daa122b3576c1a6e6e192a4992549e704721bb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="dae8c-102">IHostTaskManager::CallNeedsHostHook — Metoda</span><span class="sxs-lookup"><span data-stu-id="dae8c-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="dae8c-103">Umożliwia hosta określić, czy środowisko uruchomieniowe języka wspólnego (CLR) może wbudowanego określonego wywołanie funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="dae8c-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae8c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dae8c-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dae8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dae8c-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="dae8c-106">[in] Adres w pliku mapowanego przenośny plik wykonywalny (PE) niezarządzanych funkcji, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="dae8c-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="dae8c-107">[out] Wskaźnik na wartość logiczną, wskazującą, czy host wymaga wywołania być punktem zaczepienia.</span><span class="sxs-lookup"><span data-stu-id="dae8c-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dae8c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dae8c-108">Return Value</span></span>  
  
|<span data-ttu-id="dae8c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dae8c-109">HRESULT</span></span>|<span data-ttu-id="dae8c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="dae8c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dae8c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dae8c-111">S_OK</span></span>|<span data-ttu-id="dae8c-112">`CallNeedsHostHook`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dae8c-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="dae8c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dae8c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dae8c-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dae8c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dae8c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dae8c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dae8c-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dae8c-116">The call timed out.</span></span>|  
|<span data-ttu-id="dae8c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dae8c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dae8c-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dae8c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dae8c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dae8c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dae8c-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dae8c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dae8c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dae8c-121">E_FAIL</span></span>|<span data-ttu-id="dae8c-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dae8c-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="dae8c-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dae8c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dae8c-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dae8c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dae8c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dae8c-125">Remarks</span></span>  
 <span data-ttu-id="dae8c-126">Do optymalizowania wykonanie kodu CLR przeprowadza analizę dla każdej z platform wywołania wywołania podczas kompilacji, aby określić, czy wywołanie może być wbudowane.</span><span class="sxs-lookup"><span data-stu-id="dae8c-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="dae8c-127">`CallNeedsHostHook`Umożliwia hosta do zastąpienia tej decyzji, gdyż, że wywołanie funkcji niezarządzanej być punktem zaczepienia.</span><span class="sxs-lookup"><span data-stu-id="dae8c-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="dae8c-128">Jeśli host wymaga punktu zaczepienia, środowisko uruchomieniowe nie niewyrównane wywołania.</span><span class="sxs-lookup"><span data-stu-id="dae8c-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="dae8c-129">Host zwykle wymagają punktu zaczepienia w przypadku, gdy należy dostosować zmiennoprzecinkowy stan lub po otrzymaniu powiadomienia, że wywołanie jest wprowadzane stanu, w którym host nie może śledzić środowiska uruchomieniowego żądania dotyczące pamięci lub wszystkie blokady podjęte.</span><span class="sxs-lookup"><span data-stu-id="dae8c-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="dae8c-130">Gdy host wymaga, aby być punktem zaczepienia wywołanie, środowisko uruchomieniowe powiadamia hosta przejścia do i z kodu zarządzanego za pomocą wywołania [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), i [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="dae8c-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dae8c-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dae8c-131">Requirements</span></span>  
 <span data-ttu-id="dae8c-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae8c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae8c-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dae8c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dae8c-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dae8c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dae8c-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae8c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae8c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dae8c-136">See Also</span></span>  
 [<span data-ttu-id="dae8c-137">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="dae8c-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="dae8c-138">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="dae8c-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="dae8c-139">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="dae8c-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="dae8c-140">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="dae8c-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
