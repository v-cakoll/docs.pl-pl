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
ms.openlocfilehash: 4cd3012d966c777749eb800b8986974a4e8d401f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154170"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="35039-102">IHostTaskManager::ReverseLeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="35039-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="35039-103">Powiadamia hosta, że formant jest pozostawienie środowisko uruchomieniowe języka wspólnego (CLR) i wprowadzając niezarządzanej funkcji, która z kolei wywoływana z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="35039-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35039-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35039-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="35039-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="35039-105">Return Value</span></span>  
  
|<span data-ttu-id="35039-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35039-106">HRESULT</span></span>|<span data-ttu-id="35039-107">Opis</span><span class="sxs-lookup"><span data-stu-id="35039-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35039-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="35039-108">S_OK</span></span>|<span data-ttu-id="35039-109">`ReverseLeaveRuntime` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="35039-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="35039-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="35039-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="35039-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="35039-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="35039-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="35039-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="35039-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="35039-113">The call timed out.</span></span>|  
|<span data-ttu-id="35039-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="35039-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="35039-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="35039-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="35039-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="35039-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="35039-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="35039-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="35039-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35039-118">E_FAIL</span></span>|<span data-ttu-id="35039-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="35039-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="35039-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="35039-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="35039-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="35039-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="35039-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="35039-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="35039-123">Nie ma wystarczającej ilości pamięci jest dostępny w celu zakończenia alokacji żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="35039-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35039-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35039-124">Remarks</span></span>  
 <span data-ttu-id="35039-125">CLR wywołuje `ReverseLeaveRuntime` poinformować hosta, która zwraca aktualnie wykonywane zadanie wywołania formantu do niezarządzanej funkcji, która z kolei wywoływana z kodu zarządzanego za pośrednictwem platformy.</span><span class="sxs-lookup"><span data-stu-id="35039-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="35039-126">Każde wywołanie `ReverseLeaveRuntime` pasuje do odpowiedniego wywołania [reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="35039-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35039-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35039-127">Requirements</span></span>  
 <span data-ttu-id="35039-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35039-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35039-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35039-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35039-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35039-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35039-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35039-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35039-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35039-132">See also</span></span>

- [<span data-ttu-id="35039-133">CallNeedsHostHook, metoda</span><span class="sxs-lookup"><span data-stu-id="35039-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="35039-134">EnterRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="35039-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="35039-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="35039-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="35039-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="35039-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="35039-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="35039-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="35039-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="35039-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="35039-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="35039-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="35039-140">[Im bliżej wywołania platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="35039-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
