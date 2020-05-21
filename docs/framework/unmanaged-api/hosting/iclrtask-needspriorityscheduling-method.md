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
ms.openlocfilehash: df20e98a9e88c10bac748a5acfc91adcb133da79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762997"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="a0a61-102">ICLRTask::NeedsPriorityScheduling — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0a61-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="a0a61-103">Pobiera wartość wskazującą, czy bieżące zadanie, które jest włączane, musi być oznaczone jako wysoki priorytet do ponownego planowania.</span><span class="sxs-lookup"><span data-stu-id="a0a61-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a61-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0a61-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0a61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0a61-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="a0a61-106">[out] `true` , Jeśli host powinien próbować ponownie zaplanować bieżące wystąpienie zadania tak szybko, jak to możliwe; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="a0a61-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0a61-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0a61-107">Return Value</span></span>  
  
|<span data-ttu-id="a0a61-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0a61-108">HRESULT</span></span>|<span data-ttu-id="a0a61-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a0a61-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0a61-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0a61-110">S_OK</span></span>|<span data-ttu-id="a0a61-111">`NeedsPriorityRescheduling`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="a0a61-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="a0a61-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0a61-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0a61-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0a61-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0a61-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0a61-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0a61-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a0a61-115">The call timed out.</span></span>|  
|<span data-ttu-id="a0a61-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0a61-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0a61-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a0a61-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0a61-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0a61-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0a61-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a0a61-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0a61-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0a61-120">E_FAIL</span></span>|<span data-ttu-id="a0a61-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a0a61-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0a61-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="a0a61-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0a61-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a0a61-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0a61-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0a61-124">Remarks</span></span>  
 <span data-ttu-id="a0a61-125">W sytuacjach, gdy zadanie jest bliskie zebrania przez moduł wyrzucania elementów bezużytecznych, środowisko CLR ustawia wartość `pbNeedsPriorityScheduling` na `true` , co wskazuje na ponowne planowanie wysokiego priorytetu.</span><span class="sxs-lookup"><span data-stu-id="a0a61-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="a0a61-126">Dzięki temu host może szybko zaplanować zadanie, ograniczając jednocześnie możliwość opóźnień w wyrzucaniu elementów bezużytecznych i umożliwienie współdziałania hosta i środowiska uruchomieniowego w celu zachowania zasobów pamięci.</span><span class="sxs-lookup"><span data-stu-id="a0a61-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0a61-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0a61-127">Requirements</span></span>  
 <span data-ttu-id="a0a61-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0a61-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0a61-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a0a61-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0a61-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a0a61-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0a61-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0a61-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a61-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0a61-132">See also</span></span>

- [<span data-ttu-id="a0a61-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a0a61-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a0a61-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0a61-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a0a61-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0a61-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a0a61-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0a61-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
