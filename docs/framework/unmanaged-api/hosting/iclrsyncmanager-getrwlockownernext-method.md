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
ms.openlocfilehash: e5a8f69e66bb4b6373aea2c753bff9351bff8128
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762490"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="e66e3-102">ICLRSyncManager::GetRWLockOwnerNext — Metoda</span><span class="sxs-lookup"><span data-stu-id="e66e3-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="e66e3-103">Pobiera następne wystąpienie [IHostTask](ihosttask-interface.md) , które jest blokowane na bieżącym zablokowaniu czytnika czytelników.</span><span class="sxs-lookup"><span data-stu-id="e66e3-103">Gets the next [IHostTask](ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e66e3-104">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e66e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e66e3-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="e66e3-106">podczas Iterator, który został utworzony przy użyciu wywołania do [CreateRWLockOwnerIterator —](iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="e66e3-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="e66e3-107">określoną Wskaźnik do następnego `IHostTask` , który czeka na blokadę, lub wartość null, jeśli żadne zadanie nie oczekuje.</span><span class="sxs-lookup"><span data-stu-id="e66e3-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e66e3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e66e3-108">Return Value</span></span>  
  
|<span data-ttu-id="e66e3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e66e3-109">HRESULT</span></span>|<span data-ttu-id="e66e3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e66e3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e66e3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e66e3-111">S_OK</span></span>|<span data-ttu-id="e66e3-112">`GetRWLockOwnerNext`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="e66e3-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="e66e3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e66e3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e66e3-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e66e3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e66e3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e66e3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e66e3-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e66e3-116">The call timed out.</span></span>|  
|<span data-ttu-id="e66e3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e66e3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e66e3-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e66e3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e66e3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e66e3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e66e3-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="e66e3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e66e3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e66e3-121">E_FAIL</span></span>|<span data-ttu-id="e66e3-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e66e3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e66e3-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="e66e3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e66e3-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e66e3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e66e3-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e66e3-125">Remarks</span></span>  
 <span data-ttu-id="e66e3-126">Jeśli `ppOwnerHostTask` jest ustawiona na wartość null, iteracja została zakończona, a host powinien wywołać metodę [DeleteRWLockOwnerIterator —](iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e66e3-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e66e3-127">Środowisko CLR wywołuje `AddRef` na, `IHostTask` które `ppOwnerHostTask` punkty uniemożliwiają zakończenie tego zadania, gdy host utrzymuje wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="e66e3-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="e66e3-128">Host musi wywołać `Release` , aby zmniejszyć liczbę odwołań po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e66e3-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e66e3-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e66e3-129">Requirements</span></span>  
 <span data-ttu-id="e66e3-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e66e3-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e66e3-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e66e3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e66e3-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e66e3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e66e3-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e66e3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66e3-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e66e3-134">See also</span></span>

- [<span data-ttu-id="e66e3-135">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e66e3-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e66e3-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e66e3-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
