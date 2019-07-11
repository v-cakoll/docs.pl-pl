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
ms.openlocfilehash: 920aecab03e386a48f59843b26610cf260419293
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749441"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="e413b-102">IHostTaskManager::ReverseLeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="e413b-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="e413b-103">Powiadamia hosta, że formant jest pozostawienie środowisko uruchomieniowe języka wspólnego (CLR) i wprowadzając niezarządzanej funkcji, która z kolei wywoływana z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e413b-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e413b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e413b-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e413b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e413b-105">Return Value</span></span>  
  
|<span data-ttu-id="e413b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e413b-106">HRESULT</span></span>|<span data-ttu-id="e413b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e413b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e413b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e413b-108">S_OK</span></span>|<span data-ttu-id="e413b-109">`ReverseLeaveRuntime` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e413b-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="e413b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e413b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e413b-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e413b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e413b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e413b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e413b-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e413b-113">The call timed out.</span></span>|  
|<span data-ttu-id="e413b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e413b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e413b-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e413b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e413b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e413b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e413b-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e413b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e413b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e413b-118">E_FAIL</span></span>|<span data-ttu-id="e413b-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e413b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e413b-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e413b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e413b-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e413b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e413b-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e413b-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e413b-123">Nie ma wystarczającej ilości pamięci jest dostępny w celu zakończenia alokacji żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="e413b-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e413b-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e413b-124">Remarks</span></span>  
 <span data-ttu-id="e413b-125">CLR wywołuje `ReverseLeaveRuntime` poinformować hosta, która zwraca aktualnie wykonywane zadanie wywołania formantu do niezarządzanej funkcji, która z kolei wywoływana z kodu zarządzanego za pośrednictwem platformy.</span><span class="sxs-lookup"><span data-stu-id="e413b-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="e413b-126">Każde wywołanie `ReverseLeaveRuntime` pasuje do odpowiedniego wywołania [reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="e413b-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e413b-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e413b-127">Requirements</span></span>  
 <span data-ttu-id="e413b-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e413b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e413b-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e413b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e413b-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e413b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e413b-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e413b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e413b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e413b-132">See also</span></span>

- [<span data-ttu-id="e413b-133">CallNeedsHostHook, metoda</span><span class="sxs-lookup"><span data-stu-id="e413b-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="e413b-134">EnterRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="e413b-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="e413b-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e413b-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e413b-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e413b-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e413b-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e413b-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e413b-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e413b-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="e413b-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="e413b-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="e413b-140">[Im bliżej wywołania platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e413b-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
