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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165311"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="86cde-102">ICLRTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="86cde-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="86cde-103">Pobiera [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia, które jest aktualnie uruchomione w wątku systemu operacyjnego, z którego pochodzi wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="86cde-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cde-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86cde-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86cde-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86cde-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="86cde-106">[out] Wskaźnik na adres `ICLRTask` wystąpienie, które jest obecnie wykonywany w wątku systemu operacyjnego, z którego pochodzi wywołania lub wartość null, jeśli zadanie nie jest obecnie wykonywany w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="86cde-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86cde-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="86cde-107">Return Value</span></span>  
  
|<span data-ttu-id="86cde-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86cde-108">HRESULT</span></span>|<span data-ttu-id="86cde-109">Opis</span><span class="sxs-lookup"><span data-stu-id="86cde-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86cde-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="86cde-110">S_OK</span></span>|<span data-ttu-id="86cde-111">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="86cde-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="86cde-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86cde-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86cde-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="86cde-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86cde-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86cde-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86cde-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="86cde-115">The call timed out.</span></span>|  
|<span data-ttu-id="86cde-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86cde-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86cde-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="86cde-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86cde-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86cde-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86cde-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="86cde-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86cde-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86cde-120">E_FAIL</span></span>|<span data-ttu-id="86cde-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="86cde-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86cde-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="86cde-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86cde-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="86cde-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86cde-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86cde-124">Remarks</span></span>  
 <span data-ttu-id="86cde-125">`ICLRTask` Wystąpienie, które `ppTask` parametr wskazuje reprezentuje aktualnie wykonywane zadanie dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="86cde-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="86cde-126">`ICLRTask` Wystąpienia jest skojarzony z odpowiednią [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, która reprezentuje zadania dla hosta.</span><span class="sxs-lookup"><span data-stu-id="86cde-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86cde-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86cde-127">Requirements</span></span>  
 <span data-ttu-id="86cde-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86cde-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86cde-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86cde-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86cde-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86cde-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="86cde-131">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="86cde-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86cde-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86cde-132">See also</span></span>

- [<span data-ttu-id="86cde-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86cde-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="86cde-134">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86cde-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="86cde-135">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86cde-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="86cde-136">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86cde-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
