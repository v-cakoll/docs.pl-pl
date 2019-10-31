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
ms.openlocfilehash: bbb563a304e3ff7cdba3dfe7e394da9cf138ff10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121369"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="934df-102">IHostTask::SetCLRTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="934df-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="934df-103">Kojarzy wystąpienie `ICLRTask` z bieżącym wystąpieniem [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="934df-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="934df-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="934df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="934df-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="934df-106">podczas Wskaźnik interfejsu do wystąpienia `ICLRTask`, który ma zostać skojarzony z bieżącym wystąpieniem `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="934df-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="934df-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="934df-107">Return Value</span></span>  
  
|<span data-ttu-id="934df-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="934df-108">HRESULT</span></span>|<span data-ttu-id="934df-109">Opis</span><span class="sxs-lookup"><span data-stu-id="934df-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="934df-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="934df-110">S_OK</span></span>|<span data-ttu-id="934df-111">`SetCLRTask` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="934df-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="934df-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="934df-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="934df-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="934df-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="934df-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="934df-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="934df-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="934df-115">The call timed out.</span></span>|  
|<span data-ttu-id="934df-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="934df-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="934df-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="934df-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="934df-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="934df-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="934df-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="934df-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="934df-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="934df-120">E_FAIL</span></span>|<span data-ttu-id="934df-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="934df-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="934df-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="934df-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="934df-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="934df-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="934df-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="934df-124">Remarks</span></span>  
 <span data-ttu-id="934df-125">Wywołania CLR `SetCLRTask` do skojarzenia wystąpienia `ICLRTask` z bieżącym wystąpieniem `IHostTask`, które zostało utworzone przez wywołanie [IHostTaskManager::](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)CreateInstance.</span><span class="sxs-lookup"><span data-stu-id="934df-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934df-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="934df-126">Requirements</span></span>  
 <span data-ttu-id="934df-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934df-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934df-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="934df-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="934df-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="934df-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="934df-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934df-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934df-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="934df-131">See also</span></span>

- [<span data-ttu-id="934df-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="934df-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="934df-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="934df-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="934df-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
