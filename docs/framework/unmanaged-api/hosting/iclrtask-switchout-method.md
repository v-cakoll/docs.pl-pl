---
title: ICLRTask::SwitchOut — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: f9c2e77013ff9e31a0a2ef3b4ca511b76ae345e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124597"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="2e817-102">ICLRTask::SwitchOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e817-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="2e817-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), że zadanie reprezentowane przez bieżące wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) nie jest już w stanie obsługiwanym.</span><span class="sxs-lookup"><span data-stu-id="2e817-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e817-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e817-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2e817-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2e817-105">Return Value</span></span>  
  
|<span data-ttu-id="2e817-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e817-106">HRESULT</span></span>|<span data-ttu-id="2e817-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2e817-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e817-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e817-108">S_OK</span></span>|<span data-ttu-id="2e817-109">`SwitchOut` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="2e817-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="2e817-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e817-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e817-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2e817-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e817-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e817-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e817-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2e817-113">The call timed out.</span></span>|  
|<span data-ttu-id="2e817-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e817-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e817-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2e817-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e817-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e817-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e817-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2e817-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e817-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e817-118">E_FAIL</span></span>|<span data-ttu-id="2e817-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2e817-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e817-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="2e817-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e817-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2e817-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e817-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e817-122">Remarks</span></span>  
 <span data-ttu-id="2e817-123">Host wywołuje `SwitchOut`, aby poinformować środowisko CLR o tymczasowym zatrzymaniu wykonywania zadania, które reprezentuje bieżące wystąpienie `ICLRTask`, i ponownie planuje zadanie.</span><span class="sxs-lookup"><span data-stu-id="2e817-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e817-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e817-124">Requirements</span></span>  
 <span data-ttu-id="2e817-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e817-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e817-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e817-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e817-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e817-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e817-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e817-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e817-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e817-129">See also</span></span>

- [<span data-ttu-id="2e817-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e817-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2e817-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e817-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2e817-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e817-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2e817-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e817-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
