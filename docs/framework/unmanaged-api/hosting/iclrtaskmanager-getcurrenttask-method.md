---
title: ICLRTaskManager::GetCurrentTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db333cd97963ca8ef26673c0ba5cbf352fa331b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165311"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="62c7c-102">ICLRTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="62c7c-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="62c7c-103">Pobiera [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia, które jest aktualnie uruchomione w wątku systemu operacyjnego, z którego pochodzi wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="62c7c-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c7c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62c7c-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62c7c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62c7c-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="62c7c-106">[out] Wskaźnik na adres `ICLRTask` wystąpienie, które jest obecnie wykonywany w wątku systemu operacyjnego, z którego pochodzi wywołania lub wartość null, jeśli zadanie nie jest obecnie wykonywany w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="62c7c-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62c7c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62c7c-107">Return Value</span></span>  
  
|<span data-ttu-id="62c7c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62c7c-108">HRESULT</span></span>|<span data-ttu-id="62c7c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="62c7c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62c7c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="62c7c-110">S_OK</span></span>|<span data-ttu-id="62c7c-111">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="62c7c-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="62c7c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62c7c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62c7c-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="62c7c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62c7c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62c7c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62c7c-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="62c7c-115">The call timed out.</span></span>|  
|<span data-ttu-id="62c7c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62c7c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62c7c-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="62c7c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62c7c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62c7c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62c7c-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="62c7c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62c7c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62c7c-120">E_FAIL</span></span>|<span data-ttu-id="62c7c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="62c7c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62c7c-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="62c7c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62c7c-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="62c7c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62c7c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62c7c-124">Remarks</span></span>  
 <span data-ttu-id="62c7c-125">`ICLRTask` Wystąpienie, które `ppTask` parametr wskazuje reprezentuje aktualnie wykonywane zadanie dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="62c7c-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="62c7c-126">`ICLRTask` Wystąpienia jest skojarzony z odpowiednią [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, która reprezentuje zadania dla hosta.</span><span class="sxs-lookup"><span data-stu-id="62c7c-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62c7c-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62c7c-127">Requirements</span></span>  
 <span data-ttu-id="62c7c-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62c7c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62c7c-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62c7c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62c7c-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62c7c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62c7c-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62c7c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c7c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62c7c-132">See also</span></span>

- [<span data-ttu-id="62c7c-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="62c7c-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="62c7c-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="62c7c-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="62c7c-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="62c7c-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="62c7c-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="62c7c-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
