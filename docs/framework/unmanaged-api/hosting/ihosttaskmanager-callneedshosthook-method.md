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
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176295"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="f7132-102">IHostTaskManager::CallNeedsHostHook — Metoda</span><span class="sxs-lookup"><span data-stu-id="f7132-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="f7132-103">Umożliwia hostowi określenie, czy środowisko uruchomieniowe języka wspólnego (CLR) może wbudowane określone wywołanie funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f7132-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7132-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7132-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7132-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7132-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="f7132-106">[w] Adres w mapowanym pliku wykonywalnego przenośnego (PE) niezarządzanej funkcji, która ma być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f7132-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="f7132-107">[na zewnątrz] Wskaźnik do wartości logicznej, który wskazuje, czy host wymaga połączenia, które mają być podłączone.</span><span class="sxs-lookup"><span data-stu-id="f7132-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7132-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f7132-108">Return Value</span></span>  
  
|<span data-ttu-id="f7132-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7132-109">HRESULT</span></span>|<span data-ttu-id="f7132-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f7132-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7132-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7132-111">S_OK</span></span>|<span data-ttu-id="f7132-112">`CallNeedsHostHook`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f7132-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="f7132-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7132-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7132-114">Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f7132-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7132-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7132-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f7132-116">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f7132-116">The call timed out.</span></span>|  
|<span data-ttu-id="f7132-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f7132-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f7132-118">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f7132-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f7132-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f7132-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f7132-120">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="f7132-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f7132-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="f7132-121">E_FAIL</span></span>|<span data-ttu-id="f7132-122">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="f7132-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="f7132-123">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f7132-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7132-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f7132-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7132-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7132-125">Remarks</span></span>  
 <span data-ttu-id="f7132-126">Aby zoptymalizować wykonanie kodu, CLR wykonuje analizę każdej platformy wywołać wywołanie podczas kompilacji, aby ustalić, czy wywołanie może być inlined.</span><span class="sxs-lookup"><span data-stu-id="f7132-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="f7132-127">`CallNeedsHostHook`umożliwia hostowi zastąpienie tej decyzji, wymagając podłączenia wywołania funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f7132-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="f7132-128">Jeśli host wymaga haka, środowisko wykonawcze nie inline wywołania.</span><span class="sxs-lookup"><span data-stu-id="f7132-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="f7132-129">Host zazwyczaj wymaga haka, gdzie musi dostosować stan zmiennoprzecinkowe lub po otrzymaniu powiadomienia, że wywołanie jest wprowadzenie stanu, w którym host nie może śledzić żądania środowiska wykonawczego dla pamięci lub blokady podjęte.</span><span class="sxs-lookup"><span data-stu-id="f7132-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="f7132-130">Gdy host wymaga, aby wywołanie zostało podłączona, środowisko wykonawcze powiadamia o wielu przejściach do i z kodu zarządzanego przy użyciu wywołań [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)i [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="f7132-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7132-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7132-131">Requirements</span></span>  
 <span data-ttu-id="f7132-132">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7132-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7132-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7132-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7132-134">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7132-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7132-135">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7132-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7132-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7132-136">See also</span></span>

- [<span data-ttu-id="f7132-137">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f7132-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f7132-138">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7132-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f7132-139">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7132-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f7132-140">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7132-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
