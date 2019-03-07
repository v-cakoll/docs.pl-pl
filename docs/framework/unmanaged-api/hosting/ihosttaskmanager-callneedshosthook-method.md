---
title: IHostTaskManager::CallNeedsHostHook — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fa5807a52565a5444334b313dc8dfa315a15c13
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480562"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="2ecae-102">IHostTaskManager::CallNeedsHostHook — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ecae-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="2ecae-103">Umożliwia hosta określić, czy środowisko uruchomieniowe języka wspólnego (CLR) można wbudowane określone wywołanie do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ecae-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ecae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ecae-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ecae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ecae-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="2ecae-106">[in] Adres w ramach pliku mapowanego przenośny plik wykonywalny (PE) niezarządzanej funkcji, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="2ecae-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="2ecae-107">[out] Wskaźnik na wartość logiczną, wskazującą, czy host wymaga wywołania być dołączane.</span><span class="sxs-lookup"><span data-stu-id="2ecae-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ecae-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ecae-108">Return Value</span></span>  
  
|<span data-ttu-id="2ecae-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ecae-109">HRESULT</span></span>|<span data-ttu-id="2ecae-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2ecae-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ecae-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ecae-111">S_OK</span></span>|<span data-ttu-id="2ecae-112">`CallNeedsHostHook` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="2ecae-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="2ecae-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ecae-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ecae-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="2ecae-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ecae-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ecae-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ecae-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="2ecae-116">The call timed out.</span></span>|  
|<span data-ttu-id="2ecae-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ecae-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ecae-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="2ecae-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ecae-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ecae-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ecae-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="2ecae-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ecae-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ecae-121">E_FAIL</span></span>|<span data-ttu-id="2ecae-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2ecae-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="2ecae-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="2ecae-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ecae-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2ecae-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ecae-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ecae-125">Remarks</span></span>  
 <span data-ttu-id="2ecae-126">Aby pomóc zoptymalizować wykonywania kodu, CLR wykonuje analizę każdej z platform wywołania wywołania podczas kompilacji, aby ustalić, czy wywołanie może być śródwierszowa.</span><span class="sxs-lookup"><span data-stu-id="2ecae-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="2ecae-127">`CallNeedsHostHook` Umożliwia hosta do zastąpienia decyzji, wymagając, że wywołanie funkcji niezarządzanej być dołączane.</span><span class="sxs-lookup"><span data-stu-id="2ecae-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="2ecae-128">Jeśli host wymaga zaczepienia, środowisko wykonawcze nie niewyrównane wywołania.</span><span class="sxs-lookup"><span data-stu-id="2ecae-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="2ecae-129">Host zazwyczaj wymagałoby zaczepienia w przypadku, gdy należy dostosować, stan zapisu zmiennoprzecinkowego lub po otrzymaniu powiadomienia, że wywołanie jest wprowadzane stanu, gdy host nie może śledzić żądania w środowisku uruchomieniowym pamięci lub wszystkie blokady podjęte.</span><span class="sxs-lookup"><span data-stu-id="2ecae-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="2ecae-130">Gdy host wymaga, że wywołanie być dołączane, środowisko uruchomieniowe powiadamia hosta przejścia do i z kodu zarządzanego za pomocą wywołania [enterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [leaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ Reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), i [reverseleaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="2ecae-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ecae-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ecae-131">Requirements</span></span>  
 <span data-ttu-id="2ecae-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ecae-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ecae-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ecae-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ecae-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ecae-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ecae-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ecae-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ecae-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ecae-136">See also</span></span>
- [<span data-ttu-id="2ecae-137">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ecae-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2ecae-138">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ecae-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2ecae-139">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ecae-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2ecae-140">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ecae-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
