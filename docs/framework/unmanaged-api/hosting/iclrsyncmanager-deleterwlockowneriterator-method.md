---
title: ICLRSyncManager::DeleteRWLockOwnerIterator — Metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: fb02b5c941e15d172140565e8efb625234947cd7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130578"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="7b06c-102">ICLRSyncManager::DeleteRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="7b06c-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="7b06c-103">Żądania, dla których środowisko uruchomieniowe języka wspólnego (CLR) niszczy iterator, który został utworzony przez wywołanie [ICLRSyncManager:: CreateRWLockOwnerIterator —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="7b06c-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b06c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b06c-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b06c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b06c-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="7b06c-106">podczas Iterator, który został utworzony przy użyciu wywołania do `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="7b06c-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b06c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7b06c-107">Return Value</span></span>  
  
|<span data-ttu-id="7b06c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b06c-108">HRESULT</span></span>|<span data-ttu-id="7b06c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7b06c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b06c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b06c-110">S_OK</span></span>|<span data-ttu-id="7b06c-111">`DeleteRWLockOwnerIterator` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7b06c-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="7b06c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b06c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b06c-113">Środowisko CLR nie zostało załadowane do procesu lub znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub pomyślnie przetworzył wywołanie.</span><span class="sxs-lookup"><span data-stu-id="7b06c-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="7b06c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b06c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b06c-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="7b06c-115">The call timed out.</span></span>|  
|<span data-ttu-id="7b06c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b06c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b06c-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7b06c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b06c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b06c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b06c-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="7b06c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b06c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b06c-120">E_FAIL</span></span>|<span data-ttu-id="7b06c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7b06c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b06c-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="7b06c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b06c-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b06c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b06c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b06c-124">Remarks</span></span>  
 <span data-ttu-id="7b06c-125">Host może wywołać tę metodę i `CreateRWLockOwnerIterator`, aby upewnić się, że jej implementacja wielowątkowości pozostanie zsynchronizowana.</span><span class="sxs-lookup"><span data-stu-id="7b06c-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b06c-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b06c-126">Requirements</span></span>  
 <span data-ttu-id="7b06c-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b06c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b06c-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7b06c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b06c-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7b06c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b06c-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b06c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b06c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b06c-131">See also</span></span>

- [<span data-ttu-id="7b06c-132">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b06c-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="7b06c-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b06c-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
