---
title: IHostTaskManager::EndThreadAffinity — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: c40febb78c1bc78a5a724f559eb95869e90bdad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133086"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="934df-102">IHostTaskManager::EndThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="934df-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="934df-103">Powiadamia hosta, że kod zarządzany kończy okres, w którym bieżące zadanie nie może zostać przeniesione do innego wątku systemu operacyjnego, po wcześniejszym wywołaniu [IHostTaskManager:: BeginThreadAffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="934df-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="934df-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="934df-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="934df-105">Return Value</span></span>  
  
|<span data-ttu-id="934df-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="934df-106">HRESULT</span></span>|<span data-ttu-id="934df-107">Opis</span><span class="sxs-lookup"><span data-stu-id="934df-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="934df-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="934df-108">S_OK</span></span>|<span data-ttu-id="934df-109">`EndThreadAffinity` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="934df-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="934df-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="934df-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="934df-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="934df-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="934df-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="934df-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="934df-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="934df-113">The call timed out.</span></span>|  
|<span data-ttu-id="934df-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="934df-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="934df-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="934df-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="934df-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="934df-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="934df-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="934df-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="934df-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="934df-118">E_FAIL</span></span>|<span data-ttu-id="934df-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="934df-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="934df-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="934df-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="934df-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="934df-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="934df-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="934df-122">E_UNEXPECTED</span></span>|<span data-ttu-id="934df-123">`EndThreadAffinity` został wywołany bez wcześniejszego wywołania do `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="934df-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="934df-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="934df-124">Remarks</span></span>  
 <span data-ttu-id="934df-125">Środowisko CLR tworzy odpowiednie wywołanie `BeginThreadAffinity` w bieżącym zadaniu przed wywołaniem `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="934df-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="934df-126">W przypadku braku takiego wywołania implementacja hosta [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) powinna zwrócić E_UNEXPECTED i nie podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="934df-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934df-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="934df-127">Requirements</span></span>  
 <span data-ttu-id="934df-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934df-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934df-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="934df-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="934df-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="934df-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="934df-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934df-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934df-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="934df-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="934df-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="934df-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="934df-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="934df-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
