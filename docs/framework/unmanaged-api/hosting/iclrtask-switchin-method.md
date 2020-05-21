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
ms.openlocfilehash: d8f57af459d1bb3f338cfbfcbb29f69f533ea927
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762932"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="fa7b2-102">ICLRTask::SwitchIn — Metoda</span><span class="sxs-lookup"><span data-stu-id="fa7b2-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="fa7b2-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o tym, że zadanie, które reprezentuje bieżące wystąpienie [ICLRTask](iclrtask-interface.md) , jest teraz w stanie nieobsługiwanym.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa7b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa7b2-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa7b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa7b2-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="fa7b2-106">podczas Dojście do wątku fizycznego, w którym wykonywane jest zadanie reprezentowane przez bieżące `ICLRTask` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa7b2-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa7b2-107">Return Value</span></span>  
  
|<span data-ttu-id="fa7b2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa7b2-108">HRESULT</span></span>|<span data-ttu-id="fa7b2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fa7b2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa7b2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa7b2-110">S_OK</span></span>|<span data-ttu-id="fa7b2-111">`SwitchIn`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="fa7b2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa7b2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa7b2-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa7b2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa7b2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa7b2-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-115">The call timed out.</span></span>|  
|<span data-ttu-id="fa7b2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa7b2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa7b2-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa7b2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa7b2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa7b2-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa7b2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa7b2-120">E_FAIL</span></span>|<span data-ttu-id="fa7b2-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa7b2-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa7b2-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fa7b2-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="fa7b2-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="fa7b2-125">`SwitchIn`został wywołany bez wcześniejszego wywołania [metody SwitchOut —](iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="fa7b2-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa7b2-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa7b2-126">Remarks</span></span>  
 <span data-ttu-id="fa7b2-127">`threadHandle`Parametr reprezentuje dojście do wątku systemu operacyjnego, w którym zaplanowano zadanie reprezentowane przez bieżące `ICLRTask` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="fa7b2-128">W przypadku wystąpienia personifikacji w tym wątku należy wywołać metodę [IHostSecurityManager:: RevertToSelf —](ihostsecuritymanager-reverttoself-method.md) przed przełączeniem w zadaniu.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa7b2-129">Wywołanie `SwitchIn` bez wcześniejszego wywołania do `SwitchOut` nie powiodło się z wartością HRESULT wynoszącą HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa7b2-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa7b2-130">Requirements</span></span>  
 <span data-ttu-id="fa7b2-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa7b2-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa7b2-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fa7b2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa7b2-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fa7b2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa7b2-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa7b2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7b2-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa7b2-135">See also</span></span>

- [<span data-ttu-id="fa7b2-136">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b2-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fa7b2-137">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b2-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fa7b2-138">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b2-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fa7b2-139">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b2-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
