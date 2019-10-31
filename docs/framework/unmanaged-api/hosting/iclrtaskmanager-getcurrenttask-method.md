---
title: ICLRTaskManager::GetCurrentTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: a57610d1b41d80d54a245b9744aafd78a1e88177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195910"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="81f9a-102">ICLRTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="81f9a-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="81f9a-103">Pobiera wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) , które jest aktualnie uruchomione w wątku systemu operacyjnego, z którego pochodzi wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="81f9a-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81f9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81f9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81f9a-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="81f9a-106">określoną Wskaźnik do adresu `ICLRTask` wystąpienia, które jest aktualnie wykonywane w wątku systemu operacyjnego, z którego pochodzi wywołanie lub wartość null, jeśli żadne zadanie nie jest aktualnie wykonywane w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="81f9a-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81f9a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81f9a-107">Return Value</span></span>  
  
|<span data-ttu-id="81f9a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81f9a-108">HRESULT</span></span>|<span data-ttu-id="81f9a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="81f9a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81f9a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="81f9a-110">S_OK</span></span>|<span data-ttu-id="81f9a-111">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="81f9a-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="81f9a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81f9a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81f9a-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="81f9a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81f9a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81f9a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81f9a-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="81f9a-115">The call timed out.</span></span>|  
|<span data-ttu-id="81f9a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81f9a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81f9a-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="81f9a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81f9a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81f9a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81f9a-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="81f9a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81f9a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81f9a-120">E_FAIL</span></span>|<span data-ttu-id="81f9a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="81f9a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81f9a-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="81f9a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81f9a-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="81f9a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81f9a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81f9a-124">Remarks</span></span>  
 <span data-ttu-id="81f9a-125">Wystąpienie `ICLRTask`, które wskazuje `ppTask` parametru, aby reprezentować aktualnie wykonywane zadanie dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="81f9a-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="81f9a-126">Wystąpienie `ICLRTask` jest skojarzone z odpowiednim wystąpieniem [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , które reprezentuje zadanie dla hosta.</span><span class="sxs-lookup"><span data-stu-id="81f9a-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81f9a-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81f9a-127">Requirements</span></span>  
 <span data-ttu-id="81f9a-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81f9a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81f9a-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81f9a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81f9a-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81f9a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81f9a-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81f9a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f9a-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81f9a-132">See also</span></span>

- [<span data-ttu-id="81f9a-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="81f9a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="81f9a-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="81f9a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="81f9a-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="81f9a-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="81f9a-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="81f9a-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
