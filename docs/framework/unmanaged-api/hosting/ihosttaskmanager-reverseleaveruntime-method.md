---
title: IHostTaskManager::ReverseLeaveRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0800a1441b75c5003eabc77793b2b4fa3dd8f0da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444065"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="415e5-102">IHostTaskManager::ReverseLeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="415e5-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="415e5-103">Powiadamia hosta, czy formant jest pozostawienie środowisko uruchomieniowe języka wspólnego (CLR) i wprowadzenie niezarządzanej funkcji, który z kolei wywołane z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="415e5-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="415e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="415e5-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="415e5-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="415e5-105">Return Value</span></span>  
  
|<span data-ttu-id="415e5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="415e5-106">HRESULT</span></span>|<span data-ttu-id="415e5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="415e5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="415e5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="415e5-108">S_OK</span></span>|<span data-ttu-id="415e5-109">`ReverseLeaveRuntime` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="415e5-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="415e5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="415e5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="415e5-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="415e5-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="415e5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="415e5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="415e5-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="415e5-113">The call timed out.</span></span>|  
|<span data-ttu-id="415e5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="415e5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="415e5-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="415e5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="415e5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="415e5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="415e5-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="415e5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="415e5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="415e5-118">E_FAIL</span></span>|<span data-ttu-id="415e5-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="415e5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="415e5-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="415e5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="415e5-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="415e5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="415e5-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="415e5-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="415e5-123">Do ukończenia alokacji żądany zasób jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="415e5-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="415e5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="415e5-124">Remarks</span></span>  
 <span data-ttu-id="415e5-125">Wywołania CLR `ReverseLeaveRuntime` poinformowanie hosta, która zwraca aktualnie wykonywanego zadania wywołania kontroli niezarządzanych funkcji, które z kolei wywołane z kodu zarządzanego za pośrednictwem platformy.</span><span class="sxs-lookup"><span data-stu-id="415e5-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="415e5-126">Każde wywołanie `ReverseLeaveRuntime` pasuje do odpowiedniego wywołania [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="415e5-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="415e5-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="415e5-127">Requirements</span></span>  
 <span data-ttu-id="415e5-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="415e5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="415e5-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="415e5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="415e5-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="415e5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="415e5-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="415e5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415e5-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="415e5-132">See Also</span></span>  
 [<span data-ttu-id="415e5-133">CallNeedsHostHook, metoda</span><span class="sxs-lookup"><span data-stu-id="415e5-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="415e5-134">EnterRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="415e5-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="415e5-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="415e5-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="415e5-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="415e5-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="415e5-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="415e5-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="415e5-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="415e5-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="415e5-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="415e5-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="415e5-140">Bliższe spojrzenie na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="415e5-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
