---
title: ICLRSyncManager::GetRWLockOwnerNext — Metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3efe80c0442e765274b309e39a79cc867676043
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169653"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="d0347-102">ICLRSyncManager::GetRWLockOwnerNext — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0347-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="d0347-103">Pobiera następnych [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który jest zablokowany na bieżącego czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="d0347-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0347-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0347-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0347-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0347-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="d0347-106">[in] Iterator, który został utworzony przy użyciu wywołania [createrwlockowneriterator —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="d0347-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="d0347-107">[out] Wskaźnik do następnego `IHostTask` który oczekuje na blokadę lub wartość null, jeśli zadanie nie oczekuje.</span><span class="sxs-lookup"><span data-stu-id="d0347-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0347-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0347-108">Return Value</span></span>  
  
|<span data-ttu-id="d0347-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0347-109">HRESULT</span></span>|<span data-ttu-id="d0347-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d0347-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0347-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0347-111">S_OK</span></span>|`GetRWLockOwnerNext` <span data-ttu-id="d0347-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d0347-112">returned successfully.</span></span>|  
|<span data-ttu-id="d0347-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0347-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0347-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d0347-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0347-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0347-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0347-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d0347-116">The call timed out.</span></span>|  
|<span data-ttu-id="d0347-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0347-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0347-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d0347-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0347-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0347-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0347-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d0347-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0347-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0347-121">E_FAIL</span></span>|<span data-ttu-id="d0347-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d0347-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0347-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d0347-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0347-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d0347-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0347-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0347-125">Remarks</span></span>  
 <span data-ttu-id="d0347-126">Jeśli `ppOwnerHostTask` ustawiono iteracji ma wartość null, został zakończony, a host powinien wywoływać [deleterwlockowneriterator —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d0347-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0347-127">CLR wywołuje `AddRef` na `IHostTask` do której `ppOwnerHostTask` punkty, aby uniemożliwić to zadanie zakończone podczas, gdy host przechowuje wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="d0347-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="d0347-128">Host musi wywołać `Release` zmniejszyć liczbę odwołań po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="d0347-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0347-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0347-129">Requirements</span></span>  
 <span data-ttu-id="d0347-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0347-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0347-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0347-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0347-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0347-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d0347-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d0347-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d0347-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0347-134">See also</span></span>

- [<span data-ttu-id="d0347-135">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d0347-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d0347-136">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d0347-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
