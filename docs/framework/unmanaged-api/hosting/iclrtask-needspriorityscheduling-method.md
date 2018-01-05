---
title: "ICLRTask::NeedsPriorityScheduling — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.NeedsPriorityScheduling
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ce57a4130c19ffd040bc9fbeba5e775a751efdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="59142-102">ICLRTask::NeedsPriorityScheduling — Metoda</span><span class="sxs-lookup"><span data-stu-id="59142-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="59142-103">Pobiera wartość wskazującą, czy bieżące zadanie, które jest przełączany wychodzących, musi być oznaczony jako o wysokim priorytecie przed ponownym planowaniem.</span><span class="sxs-lookup"><span data-stu-id="59142-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59142-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59142-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59142-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="59142-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="59142-106">[out] `true`, jeśli host powinien próbować zaplanować bieżącego wystąpienia zadania, jak najszybciej; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="59142-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59142-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="59142-107">Return Value</span></span>  
  
|<span data-ttu-id="59142-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59142-108">HRESULT</span></span>|<span data-ttu-id="59142-109">Opis</span><span class="sxs-lookup"><span data-stu-id="59142-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59142-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="59142-110">S_OK</span></span>|<span data-ttu-id="59142-111">`NeedsPriorityRescheduling`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="59142-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="59142-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="59142-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="59142-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="59142-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="59142-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="59142-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="59142-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="59142-115">The call timed out.</span></span>|  
|<span data-ttu-id="59142-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="59142-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="59142-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="59142-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="59142-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="59142-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="59142-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="59142-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="59142-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="59142-120">E_FAIL</span></span>|<span data-ttu-id="59142-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="59142-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="59142-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="59142-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="59142-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="59142-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59142-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59142-124">Remarks</span></span>  
 <span data-ttu-id="59142-125">W sytuacjach, gdy zadanie jest bliski zbieranych przez moduł garbage collector środowiska CLR ustawia wartość `pbNeedsPriorityScheduling` do `true`, wskazując ponowne o wysokim priorytecie.</span><span class="sxs-lookup"><span data-stu-id="59142-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="59142-126">Umożliwia hosta zmienić harmonogram zadania szybko, tym samym minimalizując potencjalnych opóźnienia w pamięci i włączenie hosta i środowiska uruchomieniowego do współpracy w celu zasobów pamięci.</span><span class="sxs-lookup"><span data-stu-id="59142-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59142-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59142-127">Requirements</span></span>  
 <span data-ttu-id="59142-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59142-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59142-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="59142-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59142-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59142-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59142-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59142-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59142-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59142-132">See Also</span></span>  
 [<span data-ttu-id="59142-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="59142-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="59142-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="59142-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="59142-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="59142-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="59142-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="59142-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
