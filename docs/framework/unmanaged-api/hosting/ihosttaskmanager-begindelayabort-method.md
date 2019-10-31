---
title: IHostTaskManager::BeginDelayAbort — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: b765d5449cebbdec5f106a8e4743fee2f0ee5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133142"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="669f4-102">IHostTaskManager::BeginDelayAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="669f4-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="669f4-103">Powiadamia hosta, że kod zarządzany wprowadza okres, w którym bieżące zadanie nie może zostać przerwane.</span><span class="sxs-lookup"><span data-stu-id="669f4-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="669f4-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="669f4-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="669f4-105">Return Value</span></span>  
  
|<span data-ttu-id="669f4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="669f4-106">HRESULT</span></span>|<span data-ttu-id="669f4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="669f4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="669f4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="669f4-108">S_OK</span></span>|<span data-ttu-id="669f4-109">`BeginDelayAbort` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="669f4-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="669f4-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="669f4-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="669f4-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="669f4-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="669f4-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="669f4-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="669f4-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="669f4-113">The call timed out.</span></span>|  
|<span data-ttu-id="669f4-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="669f4-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="669f4-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="669f4-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="669f4-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="669f4-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="669f4-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="669f4-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="669f4-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="669f4-118">E_FAIL</span></span>|<span data-ttu-id="669f4-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="669f4-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="669f4-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="669f4-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="669f4-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="669f4-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="669f4-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="669f4-122">E_UNEXPECTED</span></span>|<span data-ttu-id="669f4-123">`BeginDelayAbort` zostało już wywołane, ale odpowiednie wywołanie do [EndDelayAbort —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) nie zostało jeszcze odebrane.</span><span class="sxs-lookup"><span data-stu-id="669f4-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="669f4-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="669f4-124">Remarks</span></span>  
 <span data-ttu-id="669f4-125">Host nie może przerwać bieżącego zadania, dopóki nie zostanie wywołane `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="669f4-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="669f4-126">Jeśli inne wywołanie `BeginDelayAbort` zostało wykonane bez wywołania wywołującego do `EndDelayAbort`, host powinien zwrócić E_UNEXPECTED z `BeginDelayAbort`i nie powinien podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="669f4-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="669f4-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="669f4-127">Requirements</span></span>  
 <span data-ttu-id="669f4-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="669f4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="669f4-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="669f4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="669f4-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="669f4-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="669f4-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="669f4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669f4-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="669f4-132">See also</span></span>

- [<span data-ttu-id="669f4-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="669f4-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="669f4-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="669f4-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="669f4-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="669f4-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
