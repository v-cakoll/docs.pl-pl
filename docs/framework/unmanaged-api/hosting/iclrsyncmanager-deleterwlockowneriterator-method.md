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
ms.openlocfilehash: a4094a64d27072ce257341398bb49419bef9b8bb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763153"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="b5110-102">ICLRSyncManager::DeleteRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5110-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="b5110-103">Żądania, dla których środowisko uruchomieniowe języka wspólnego (CLR) niszczy iterator, który został utworzony przez wywołanie [ICLRSyncManager:: CreateRWLockOwnerIterator —](iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="b5110-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5110-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5110-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5110-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5110-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="b5110-106">podczas Iterator, który został utworzony przy użyciu wywołania do `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="b5110-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5110-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b5110-107">Return Value</span></span>  
  
|<span data-ttu-id="b5110-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5110-108">HRESULT</span></span>|<span data-ttu-id="b5110-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b5110-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5110-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5110-110">S_OK</span></span>|<span data-ttu-id="b5110-111">`DeleteRWLockOwnerIterator`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="b5110-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="b5110-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5110-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5110-113">Środowisko CLR nie zostało załadowane do procesu lub znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub pomyślnie przetworzył wywołanie.</span><span class="sxs-lookup"><span data-stu-id="b5110-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="b5110-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5110-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5110-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b5110-115">The call timed out.</span></span>|  
|<span data-ttu-id="b5110-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5110-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5110-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b5110-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5110-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5110-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5110-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b5110-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5110-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5110-120">E_FAIL</span></span>|<span data-ttu-id="b5110-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b5110-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5110-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="b5110-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5110-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b5110-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5110-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5110-124">Remarks</span></span>  
 <span data-ttu-id="b5110-125">Host może wywołać tę metodę i `CreateRWLockOwnerIterator` upewnić się, że jej implementacja wielowątkowości pozostanie zsynchronizowana.</span><span class="sxs-lookup"><span data-stu-id="b5110-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5110-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5110-126">Requirements</span></span>  
 <span data-ttu-id="b5110-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5110-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5110-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b5110-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5110-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b5110-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5110-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5110-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5110-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5110-131">See also</span></span>

- [<span data-ttu-id="b5110-132">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b5110-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="b5110-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5110-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
