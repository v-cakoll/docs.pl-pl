---
title: IHostTaskManager::EndDelayAbort — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d12e5cab41f016ddee78089dc1df1f5c942ecd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789457"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="530e5-102">IHostTaskManager::EndDelayAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="530e5-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="530e5-103">Powiadamia hosta, którego kod zarządzany jest kończone okres, w której nie można przerwać bieżące zadanie, zgodnie z wcześniejszym wywołaniem [ihosttaskmanager::begindelayabort —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="530e5-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="530e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="530e5-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="530e5-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="530e5-105">Return Value</span></span>  
  
|<span data-ttu-id="530e5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="530e5-106">HRESULT</span></span>|<span data-ttu-id="530e5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="530e5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="530e5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="530e5-108">S_OK</span></span>|<span data-ttu-id="530e5-109">`EndDelayAbort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="530e5-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="530e5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="530e5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="530e5-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="530e5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="530e5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="530e5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="530e5-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="530e5-113">The call timed out.</span></span>|  
|<span data-ttu-id="530e5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="530e5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="530e5-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="530e5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="530e5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="530e5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="530e5-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="530e5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="530e5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="530e5-118">E_FAIL</span></span>|<span data-ttu-id="530e5-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="530e5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="530e5-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="530e5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="530e5-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="530e5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="530e5-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="530e5-122">E_UNEXPECTED</span></span>|<span data-ttu-id="530e5-123">`EndDelayAbort` Wywołano bez odpowiedniego wywołania `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="530e5-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="530e5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="530e5-124">Remarks</span></span>  
 <span data-ttu-id="530e5-125">Środowisko CLR wywołuje odpowiedniego `BeginDelayAbort` na bieżące zadanie przed wywołaniem `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="530e5-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="530e5-126">W przypadku braku takich odpowiedniego wywołania implementacji hosta [ihosttaskmanager —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) powinna zwrócić wartość E_UNEXPECTED z `EndDelayAbort`i powinien podejmować żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="530e5-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="530e5-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="530e5-127">Requirements</span></span>  
 <span data-ttu-id="530e5-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="530e5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="530e5-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="530e5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="530e5-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="530e5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="530e5-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="530e5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="530e5-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="530e5-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="530e5-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="530e5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="530e5-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="530e5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="530e5-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="530e5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="530e5-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="530e5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
