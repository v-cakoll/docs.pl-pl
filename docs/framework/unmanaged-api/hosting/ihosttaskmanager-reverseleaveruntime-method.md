---
title: "IHostTaskManager::ReverseLeaveRuntime — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseLeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 634465e2d78dbac41b8791d5be44b2821744f07d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="dd0fb-102">IHostTaskManager::ReverseLeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd0fb-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="dd0fb-103">Powiadamia hosta, czy formant jest pozostawienie środowisko uruchomieniowe języka wspólnego (CLR) i wprowadzenie niezarządzanej funkcji, który z kolei wywołane z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd0fb-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dd0fb-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd0fb-105">Return Value</span></span>  
  
|<span data-ttu-id="dd0fb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd0fb-106">HRESULT</span></span>|<span data-ttu-id="dd0fb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dd0fb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd0fb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd0fb-108">S_OK</span></span>|<span data-ttu-id="dd0fb-109">`ReverseLeaveRuntime`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="dd0fb-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd0fb-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd0fb-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd0fb-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd0fb-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd0fb-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-113">The call timed out.</span></span>|  
|<span data-ttu-id="dd0fb-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd0fb-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd0fb-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd0fb-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd0fb-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd0fb-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd0fb-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd0fb-118">E_FAIL</span></span>|<span data-ttu-id="dd0fb-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd0fb-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd0fb-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dd0fb-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dd0fb-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="dd0fb-123">Do ukończenia alokacji żądany zasób jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd0fb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd0fb-124">Remarks</span></span>  
 <span data-ttu-id="dd0fb-125">Wywołania CLR `ReverseLeaveRuntime` poinformowanie hosta, która zwraca aktualnie wykonywanego zadania wywołania kontroli niezarządzanych funkcji, które z kolei wywołane z kodu zarządzanego za pośrednictwem platformy.</span><span class="sxs-lookup"><span data-stu-id="dd0fb-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="dd0fb-126">Każde wywołanie `ReverseLeaveRuntime` pasuje do odpowiedniego wywołania [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="dd0fb-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd0fb-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd0fb-127">Requirements</span></span>  
 <span data-ttu-id="dd0fb-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd0fb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd0fb-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dd0fb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd0fb-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd0fb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd0fb-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd0fb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0fb-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd0fb-132">See Also</span></span>  
 [<span data-ttu-id="dd0fb-133">CallNeedsHostHook, metoda</span><span class="sxs-lookup"><span data-stu-id="dd0fb-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="dd0fb-134">EnterRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="dd0fb-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="dd0fb-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd0fb-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="dd0fb-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd0fb-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="dd0fb-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd0fb-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="dd0fb-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd0fb-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="dd0fb-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="dd0fb-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="dd0fb-140">Bliższe spojrzenie na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="dd0fb-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
