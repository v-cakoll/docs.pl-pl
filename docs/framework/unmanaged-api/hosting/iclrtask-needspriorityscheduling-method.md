---
title: ICLRTask::NeedsPriorityScheduling — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
ms.openlocfilehash: 91c1ea51969447861ff6d0956c5714baa0054450
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124669"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="72270-102">ICLRTask::NeedsPriorityScheduling — Metoda</span><span class="sxs-lookup"><span data-stu-id="72270-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="72270-103">Pobiera wartość wskazującą, czy bieżące zadanie, które jest włączane, musi być oznaczone jako wysoki priorytet do ponownego planowania.</span><span class="sxs-lookup"><span data-stu-id="72270-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72270-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72270-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72270-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72270-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="72270-106">[out] `true`, Jeśli host powinien próbować ponownie zaplanować bieżące wystąpienie zadania najszybciej, jak to możliwe; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="72270-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72270-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="72270-107">Return Value</span></span>  
  
|<span data-ttu-id="72270-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72270-108">HRESULT</span></span>|<span data-ttu-id="72270-109">Opis</span><span class="sxs-lookup"><span data-stu-id="72270-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72270-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="72270-110">S_OK</span></span>|<span data-ttu-id="72270-111">`NeedsPriorityRescheduling` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="72270-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="72270-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72270-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72270-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="72270-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72270-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72270-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72270-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="72270-115">The call timed out.</span></span>|  
|<span data-ttu-id="72270-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72270-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72270-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="72270-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72270-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72270-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72270-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="72270-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72270-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72270-120">E_FAIL</span></span>|<span data-ttu-id="72270-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="72270-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72270-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="72270-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72270-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="72270-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72270-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72270-124">Remarks</span></span>  
 <span data-ttu-id="72270-125">W sytuacjach, gdy zadanie jest bliskie zebrania przez moduł wyrzucania elementów bezużytecznych, środowisko CLR ustawia wartość `pbNeedsPriorityScheduling` do `true`, co oznacza ponowne planowanie wysokiego priorytetu.</span><span class="sxs-lookup"><span data-stu-id="72270-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="72270-126">Dzięki temu host może szybko zaplanować zadanie, ograniczając jednocześnie możliwość opóźnień w wyrzucaniu elementów bezużytecznych i umożliwienie współdziałania hosta i środowiska uruchomieniowego w celu zachowania zasobów pamięci.</span><span class="sxs-lookup"><span data-stu-id="72270-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72270-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72270-127">Requirements</span></span>  
 <span data-ttu-id="72270-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72270-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72270-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72270-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72270-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="72270-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72270-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72270-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72270-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72270-132">See also</span></span>

- [<span data-ttu-id="72270-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="72270-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="72270-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="72270-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="72270-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="72270-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="72270-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="72270-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
