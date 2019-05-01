---
title: IHostTaskManager::ReverseEnterRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6eefdaf5dee423b0a9ae054446224a3ea97e3c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796685"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="b57e3-102">IHostTaskManager::ReverseEnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="b57e3-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="b57e3-103">Powiadamia hosta, że wywołanie odbywa się na środowisko uruchomieniowe języka wspólnego (CLR) z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="b57e3-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b57e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b57e3-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b57e3-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b57e3-105">Return Value</span></span>  
  
|<span data-ttu-id="b57e3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b57e3-106">HRESULT</span></span>|<span data-ttu-id="b57e3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b57e3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b57e3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b57e3-108">S_OK</span></span>|<span data-ttu-id="b57e3-109">`ReverseEnterRuntime` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="b57e3-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="b57e3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b57e3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b57e3-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b57e3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b57e3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b57e3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b57e3-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b57e3-113">The call timed out.</span></span>|  
|<span data-ttu-id="b57e3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b57e3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b57e3-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="b57e3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b57e3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b57e3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b57e3-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b57e3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b57e3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b57e3-118">E_FAIL</span></span>|<span data-ttu-id="b57e3-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b57e3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b57e3-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b57e3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b57e3-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b57e3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b57e3-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b57e3-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b57e3-123">Nie ma wystarczającej ilości pamięci jest dostępny w celu zakończenia alokacji żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="b57e3-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b57e3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b57e3-124">Remarks</span></span>  
 <span data-ttu-id="b57e3-125">Jeśli wywołanie do środowiska CLR jest z sekwencji, które powstały w kodzie zarządzanym, każdy wywołanie `ReverseEnterRuntime` odnosi się do wywołania [reverseleaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="b57e3-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b57e3-126">Wywołania mogą pochodzić z niezarządzanego kodu bez zagnieżdżenie.</span><span class="sxs-lookup"><span data-stu-id="b57e3-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="b57e3-127">W tym przypadku jest Brak wywołania [enterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [leaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), lub `ReverseLeaveRuntime`, a liczba wywołań `ReverseEnterRuntime` nie równa się liczba wywołań `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="b57e3-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b57e3-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b57e3-128">Requirements</span></span>  
 <span data-ttu-id="b57e3-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b57e3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b57e3-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b57e3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b57e3-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b57e3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b57e3-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b57e3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b57e3-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b57e3-133">See also</span></span>

- [<span data-ttu-id="b57e3-134">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b57e3-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b57e3-135">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b57e3-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b57e3-136">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b57e3-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b57e3-137">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b57e3-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
