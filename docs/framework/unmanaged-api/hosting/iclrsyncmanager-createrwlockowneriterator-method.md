---
title: ICLRSyncManager::CreateRWLockOwnerIterator — Metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: 9eace3e7330d3f8c0c9762e0b1b456ad1bf8a3ac
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763192"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="b6abe-102">ICLRSyncManager::CreateRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6abe-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="b6abe-103">Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) tworzy iterator dla hosta do użycia w celu określenia zestawu zadań oczekujących na blokadę modułu odczytującego.</span><span class="sxs-lookup"><span data-stu-id="b6abe-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6abe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6abe-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6abe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6abe-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="b6abe-106">podczas Plik cookie skojarzony z wymaganą blokadą czytnika czytników.</span><span class="sxs-lookup"><span data-stu-id="b6abe-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="b6abe-107">określoną Wskaźnik do iteratora, który może być przesłany do metod [GetRWLockOwnerNext —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) i [DeleteRWLockOwnerIterator —](iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6abe-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6abe-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b6abe-108">Return Value</span></span>  
  
|<span data-ttu-id="b6abe-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6abe-109">HRESULT</span></span>|<span data-ttu-id="b6abe-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b6abe-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6abe-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6abe-111">S_OK</span></span>|<span data-ttu-id="b6abe-112">`CreateRWLockOwnerIterator`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="b6abe-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="b6abe-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6abe-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6abe-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b6abe-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b6abe-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b6abe-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b6abe-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b6abe-116">The call timed out.</span></span>|  
|<span data-ttu-id="b6abe-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b6abe-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b6abe-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b6abe-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b6abe-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b6abe-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b6abe-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b6abe-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b6abe-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6abe-121">E_FAIL</span></span>|<span data-ttu-id="b6abe-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b6abe-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b6abe-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="b6abe-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b6abe-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b6abe-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b6abe-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b6abe-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b6abe-126">`CreateRWLockOwnerIterator`został wywołany w wątku, w którym aktualnie działa kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b6abe-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6abe-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6abe-127">Remarks</span></span>  
 <span data-ttu-id="b6abe-128">Hosty zwykle wywołują `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` metody,, i `GetRWLockOwnerNext` podczas wykrywania zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="b6abe-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="b6abe-129">Host jest odpowiedzialny za zapewnienie, że blokada czytnika czytników jest nadal prawidłowa, ponieważ środowisko CLR nie podejmuje próby utrzymania aktywności blokady czytnika.</span><span class="sxs-lookup"><span data-stu-id="b6abe-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="b6abe-130">Dla hosta jest dostępnych kilka strategii zapewniających prawidłowość blokady:</span><span class="sxs-lookup"><span data-stu-id="b6abe-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="b6abe-131">Host może blokować wywołania wydania na blokadzie czytnika czytników (na przykład [IHostSemaphore:: ReleaseSemaphore —](ihostsemaphore-releasesemaphore-method.md)), a jednocześnie upewniając się, że ten blok nie powoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="b6abe-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="b6abe-132">Host może zablokować wyjście przed oczekiwaniem na obiekt zdarzenia skojarzony z blokadą modułu odczytującego czytnika i ponownie upewniając się, że ten blok nie powoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="b6abe-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6abe-133">`CreateRWLockOwnerIterator`musi być wywoływana tylko w wątkach, które aktualnie wykonuje kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="b6abe-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6abe-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6abe-134">Requirements</span></span>  
 <span data-ttu-id="b6abe-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6abe-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6abe-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6abe-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6abe-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6abe-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6abe-138">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6abe-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6abe-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6abe-139">See also</span></span>

- [<span data-ttu-id="b6abe-140">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b6abe-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="b6abe-141">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6abe-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
