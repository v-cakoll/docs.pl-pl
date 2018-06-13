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
ms.openlocfilehash: 4725feff4645ec207be6e6afc7d1e1d38eca36ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435213"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="72e66-102">ICLRSyncManager::GetRWLockOwnerNext — Metoda</span><span class="sxs-lookup"><span data-stu-id="72e66-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="72e66-103">Pobiera następnych [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który jest zablokowany na bieżącego czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="72e66-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72e66-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72e66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72e66-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="72e66-106">[in] Iterator, który został utworzony za pomocą wywołania [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="72e66-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="72e66-107">[out] Wskaźnik do następnego `IHostTask` który oczekuje na blokadę lub wartość null, jeśli zadanie nie oczekuje.</span><span class="sxs-lookup"><span data-stu-id="72e66-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72e66-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="72e66-108">Return Value</span></span>  
  
|<span data-ttu-id="72e66-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72e66-109">HRESULT</span></span>|<span data-ttu-id="72e66-110">Opis</span><span class="sxs-lookup"><span data-stu-id="72e66-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72e66-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="72e66-111">S_OK</span></span>|<span data-ttu-id="72e66-112">`GetRWLockOwnerNext` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="72e66-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="72e66-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72e66-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72e66-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="72e66-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72e66-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72e66-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72e66-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="72e66-116">The call timed out.</span></span>|  
|<span data-ttu-id="72e66-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72e66-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72e66-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="72e66-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72e66-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72e66-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72e66-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="72e66-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72e66-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72e66-121">E_FAIL</span></span>|<span data-ttu-id="72e66-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="72e66-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72e66-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="72e66-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72e66-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="72e66-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72e66-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72e66-125">Remarks</span></span>  
 <span data-ttu-id="72e66-126">Jeśli `ppOwnerHostTask` ma wartość null, iteracji została zakończona, a host powinny wywoływać [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="72e66-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72e66-127">Wywołania CLR `AddRef` na `IHostTask` do której `ppOwnerHostTask` punktów, aby zapobiec tego zadania zamykania podczas hosta zawiera wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="72e66-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="72e66-128">Hosta musi wywoływać `Release` Aby zmniejszyć liczbę odwołań, po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="72e66-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e66-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72e66-129">Requirements</span></span>  
 <span data-ttu-id="72e66-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72e66-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72e66-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72e66-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72e66-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72e66-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72e66-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72e66-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e66-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72e66-134">See Also</span></span>  
 [<span data-ttu-id="72e66-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="72e66-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="72e66-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="72e66-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
