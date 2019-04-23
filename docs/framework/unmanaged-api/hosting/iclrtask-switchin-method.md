---
title: ICLRTask::SwitchIn — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f36a963417aba082667bb9fb609e0d1dcad7b09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187683"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="cd9a8-102">ICLRTask::SwitchIn — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd9a8-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="cd9a8-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), zadanie, bieżący [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) reprezentuje wystąpienie znajduje się teraz w stanie wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd9a8-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd9a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd9a8-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="cd9a8-106">[in] Uchwyt do wątku fizycznym, na którym zadanie jest reprezentowane przez bieżącą `ICLRTask` wystąpienia jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd9a8-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd9a8-107">Return Value</span></span>  
  
|<span data-ttu-id="cd9a8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd9a8-108">HRESULT</span></span>|<span data-ttu-id="cd9a8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cd9a8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd9a8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd9a8-110">S_OK</span></span>|<span data-ttu-id="cd9a8-111">`SwitchIn` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="cd9a8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd9a8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd9a8-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd9a8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd9a8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd9a8-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-115">The call timed out.</span></span>|  
|<span data-ttu-id="cd9a8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd9a8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd9a8-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd9a8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd9a8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd9a8-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd9a8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd9a8-120">E_FAIL</span></span>|<span data-ttu-id="cd9a8-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd9a8-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd9a8-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cd9a8-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="cd9a8-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="cd9a8-125">`SwitchIn` Wywołano bez wcześniejszego wywołania funkcji [switchout — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd9a8-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd9a8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd9a8-126">Remarks</span></span>  
 <span data-ttu-id="cd9a8-127">`threadHandle` Parametru reprezentuje uchwyt do wątku systemu operacyjnego, na którym zadanie jest reprezentowane przez bieżącą `ICLRTask` wystąpienie zostało zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="cd9a8-128">W przypadku personifikacji w tym wątku, należy wywołać [ihostsecuritymanager::RevertToSelf —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) przed przełączeniem w zadaniu.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd9a8-129">Wywołanie `SwitchIn` bez wcześniejszego wywołania funkcji `SwitchOut` kończy się niepowodzeniem z wartością HRESULT w HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="cd9a8-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9a8-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd9a8-130">Requirements</span></span>  
 <span data-ttu-id="cd9a8-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd9a8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9a8-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd9a8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd9a8-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd9a8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd9a8-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd9a8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9a8-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd9a8-135">See also</span></span>

- [<span data-ttu-id="cd9a8-136">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd9a8-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="cd9a8-137">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd9a8-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="cd9a8-138">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd9a8-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="cd9a8-139">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd9a8-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
