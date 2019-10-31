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
ms.openlocfilehash: f5a595651baa48553997c2cba138f4f61bd530f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133101"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="d861c-102">IHostTaskManager::CallNeedsHostHook — Metoda</span><span class="sxs-lookup"><span data-stu-id="d861c-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="d861c-103">Umożliwia hostowi określenie, czy środowisko uruchomieniowe języka wspólnego (CLR) może być wbudowane w określone wywołanie do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d861c-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d861c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d861c-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d861c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d861c-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="d861c-106">podczas Adres w zamapowanym przenośnym pliku wykonywalnym (PE) niezarządzanej funkcji, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="d861c-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="d861c-107">określoną Wskaźnik do wartości logicznej wskazującej, czy host wymaga wywołania.</span><span class="sxs-lookup"><span data-stu-id="d861c-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d861c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d861c-108">Return Value</span></span>  
  
|<span data-ttu-id="d861c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d861c-109">HRESULT</span></span>|<span data-ttu-id="d861c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d861c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d861c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d861c-111">S_OK</span></span>|<span data-ttu-id="d861c-112">`CallNeedsHostHook` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="d861c-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="d861c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d861c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d861c-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d861c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d861c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d861c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d861c-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="d861c-116">The call timed out.</span></span>|  
|<span data-ttu-id="d861c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d861c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d861c-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d861c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d861c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d861c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d861c-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="d861c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d861c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d861c-121">E_FAIL</span></span>|<span data-ttu-id="d861c-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d861c-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="d861c-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="d861c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d861c-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d861c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d861c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d861c-125">Remarks</span></span>  
 <span data-ttu-id="d861c-126">Aby ułatwić optymalizację wykonywania kodu, środowisko CLR wykonuje analizę każdego wywołania wywołania platformy podczas kompilacji, aby określić, czy wywołanie może być wbudowane.</span><span class="sxs-lookup"><span data-stu-id="d861c-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="d861c-127">`CallNeedsHostHook` umożliwia hostowi przesłonięcie tej decyzji przez wymaganie wywołania niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d861c-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="d861c-128">Jeśli host wymaga elementu Hook, środowisko uruchomieniowe nie wywołuje wywołania.</span><span class="sxs-lookup"><span data-stu-id="d861c-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="d861c-129">Host zwykle wymaga punktu zaczepienia, w którym należy dostosować stan zmiennoprzecinkowy lub po odebraniu powiadomienia, że wywołanie przejdzie do stanu, w którym host nie może śledzić żądań dotyczących pamięci lub wszelkich wykonanych blokad.</span><span class="sxs-lookup"><span data-stu-id="d861c-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="d861c-130">Gdy host wymaga, aby wywołanie było podłączane, środowisko uruchomieniowe powiadamia hosta przejść do i z kodu zarządzanego za pomocą wywołań do [EnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)i [ReverseLeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="d861c-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d861c-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d861c-131">Requirements</span></span>  
 <span data-ttu-id="d861c-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d861c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d861c-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d861c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d861c-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d861c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d861c-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d861c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d861c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d861c-136">See also</span></span>

- [<span data-ttu-id="d861c-137">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d861c-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d861c-138">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d861c-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d861c-139">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d861c-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d861c-140">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d861c-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
