---
title: IHostTask::SetCLRTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce823bd6a9ad26a705649a666aeb97dcfa0cdbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636550"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="c2832-102">IHostTask::SetCLRTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2832-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="c2832-103">Kojarzy `ICLRTask` wystąpienia z bieżącymi [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c2832-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2832-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2832-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2832-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2832-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="c2832-106">[in] Wskaźnik interfejsu do `ICLRTask` powiązanych z bieżącym wystąpieniu `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c2832-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2832-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c2832-107">Return Value</span></span>  
  
|<span data-ttu-id="c2832-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2832-108">HRESULT</span></span>|<span data-ttu-id="c2832-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c2832-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2832-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2832-110">S_OK</span></span>|<span data-ttu-id="c2832-111">`SetCLRTask` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="c2832-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="c2832-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2832-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2832-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c2832-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2832-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2832-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2832-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c2832-115">The call timed out.</span></span>|  
|<span data-ttu-id="c2832-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2832-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2832-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="c2832-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2832-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2832-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2832-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c2832-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2832-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2832-120">E_FAIL</span></span>|<span data-ttu-id="c2832-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c2832-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2832-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c2832-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2832-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2832-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2832-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2832-124">Remarks</span></span>  
 <span data-ttu-id="c2832-125">CLR wywołuje `SetCLRTask` skojarzyć `ICLRTask` wystąpienia z bieżącymi `IHostTask` wystąpienia, która została utworzona przez wywołanie [ihosttaskmanager::createtask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="c2832-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2832-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2832-126">Requirements</span></span>  
 <span data-ttu-id="c2832-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2832-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2832-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2832-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2832-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2832-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2832-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2832-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2832-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2832-131">See also</span></span>
- [<span data-ttu-id="c2832-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2832-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c2832-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2832-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c2832-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2832-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c2832-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2832-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
