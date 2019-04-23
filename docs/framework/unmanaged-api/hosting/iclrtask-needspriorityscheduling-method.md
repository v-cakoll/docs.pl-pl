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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91c7235fb8790783b05b217cad755d8eedc88971
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092696"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="fb187-102">ICLRTask::NeedsPriorityScheduling — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb187-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="fb187-103">Pobiera wartość wskazującą, czy bieżące zadanie, jest przełączany na poziomie, musi być oznaczony jako wysoki priorytet dla korzystanie z odpraw.</span><span class="sxs-lookup"><span data-stu-id="fb187-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb187-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb187-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb187-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb187-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="fb187-106">[out] `true`, jeśli host ma podejmować próbę zmienić termin egzaminu bieżące wystąpienie zadania, jak najszybciej; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="fb187-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb187-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fb187-107">Return Value</span></span>  
  
|<span data-ttu-id="fb187-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb187-108">HRESULT</span></span>|<span data-ttu-id="fb187-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fb187-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb187-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb187-110">S_OK</span></span>|<span data-ttu-id="fb187-111">`NeedsPriorityRescheduling` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="fb187-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="fb187-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb187-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb187-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fb187-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb187-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb187-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb187-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fb187-115">The call timed out.</span></span>|  
|<span data-ttu-id="fb187-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb187-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb187-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="fb187-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb187-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb187-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb187-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fb187-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb187-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb187-120">E_FAIL</span></span>|<span data-ttu-id="fb187-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fb187-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb187-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fb187-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb187-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb187-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb187-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb187-124">Remarks</span></span>  
 <span data-ttu-id="fb187-125">W sytuacjach, w którym zadanie znajduje się w pobliżu są zbierane przez moduł odśmiecania pamięci CLR ustawia wartość `pbNeedsPriorityScheduling` do `true`, wskazujący, korzystanie z odpraw o wysokim priorytecie.</span><span class="sxs-lookup"><span data-stu-id="fb187-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="fb187-126">Zezwalaj hostowi na szybko ponownie zaplanować zadanie, co minimalizuje ryzyko opóźnienia w wyrzucania elementów bezużytecznych oraz włączenie hosta i środowiska uruchomieniowego do współpracy w efektywne wykorzystanie zasobów pamięci.</span><span class="sxs-lookup"><span data-stu-id="fb187-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb187-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb187-127">Requirements</span></span>  
 <span data-ttu-id="fb187-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb187-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb187-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb187-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb187-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb187-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb187-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb187-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb187-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb187-132">See also</span></span>

- [<span data-ttu-id="fb187-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb187-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fb187-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb187-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fb187-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb187-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fb187-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb187-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
