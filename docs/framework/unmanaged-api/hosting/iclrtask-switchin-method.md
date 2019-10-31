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
ms.openlocfilehash: fbfd44c8e20bc75638d6356fe405f02790da8ac7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124617"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="b9c1a-102">ICLRTask::SwitchIn — Metoda</span><span class="sxs-lookup"><span data-stu-id="b9c1a-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="b9c1a-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o tym, że zadanie, które reprezentuje bieżące wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) , jest teraz w stanie nieobsługiwanym.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9c1a-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9c1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9c1a-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="b9c1a-106">podczas Dojście do wątku fizycznego, w którym wykonywane jest zadanie reprezentowane przez bieżące wystąpienie `ICLRTask`.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9c1a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9c1a-107">Return Value</span></span>  
  
|<span data-ttu-id="b9c1a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9c1a-108">HRESULT</span></span>|<span data-ttu-id="b9c1a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b9c1a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9c1a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9c1a-110">S_OK</span></span>|<span data-ttu-id="b9c1a-111">`SwitchIn` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="b9c1a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9c1a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9c1a-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9c1a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9c1a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9c1a-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-115">The call timed out.</span></span>|  
|<span data-ttu-id="b9c1a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9c1a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9c1a-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9c1a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9c1a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9c1a-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9c1a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9c1a-120">E_FAIL</span></span>|<span data-ttu-id="b9c1a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9c1a-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9c1a-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b9c1a-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b9c1a-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b9c1a-125">`SwitchIn` został wywołany bez wcześniejszego wywołania [metody SwitchOut —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="b9c1a-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9c1a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9c1a-126">Remarks</span></span>  
 <span data-ttu-id="b9c1a-127">Parametr `threadHandle` reprezentuje dojście do wątku systemu operacyjnego, w którym zaplanowano zadanie reprezentowane przez bieżące wystąpienie `ICLRTask`.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="b9c1a-128">W przypadku wystąpienia personifikacji w tym wątku należy wywołać metodę [IHostSecurityManager:: RevertToSelf —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) przed przełączeniem w zadaniu.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9c1a-129">Wywołanie `SwitchIn` bez wcześniejszego wywołania do `SwitchOut` kończy się niepowodzeniem z wartością HRESULT równą HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c1a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9c1a-130">Requirements</span></span>  
 <span data-ttu-id="b9c1a-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9c1a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c1a-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b9c1a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9c1a-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9c1a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9c1a-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9c1a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c1a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9c1a-135">See also</span></span>

- [<span data-ttu-id="b9c1a-136">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9c1a-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b9c1a-137">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9c1a-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b9c1a-138">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9c1a-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b9c1a-139">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9c1a-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
