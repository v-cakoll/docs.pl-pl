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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 008e76b57ed0925eaae29cf7d2b451fc9ddd08a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730103"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="70ef1-102">ICLRSyncManager::DeleteRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="70ef1-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="70ef1-103">Żąda się, że środowisko uruchomieniowe języka wspólnego (CLR) zniszczyć iterator, który został utworzony przez wywołanie [iclrsyncmanager::createrwlockowneriterator —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="70ef1-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70ef1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70ef1-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70ef1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70ef1-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="70ef1-106">[in] Iterator, który został utworzony przy użyciu wywołania `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="70ef1-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70ef1-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="70ef1-107">Return Value</span></span>  
  
|<span data-ttu-id="70ef1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70ef1-108">HRESULT</span></span>|<span data-ttu-id="70ef1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="70ef1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70ef1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="70ef1-110">S_OK</span></span>|<span data-ttu-id="70ef1-111">`DeleteRWLockOwnerIterator` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="70ef1-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="70ef1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70ef1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70ef1-113">Środowisko CLR nie został załadowany do procesu lub jest w stanie, w której nie można uruchomić kod zarządzany lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="70ef1-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="70ef1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70ef1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70ef1-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="70ef1-115">The call timed out.</span></span>|  
|<span data-ttu-id="70ef1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70ef1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70ef1-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="70ef1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70ef1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70ef1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70ef1-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="70ef1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70ef1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70ef1-120">E_FAIL</span></span>|<span data-ttu-id="70ef1-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="70ef1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70ef1-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="70ef1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70ef1-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="70ef1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70ef1-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70ef1-124">Remarks</span></span>  
 <span data-ttu-id="70ef1-125">Host może wywołać tę metodę i `CreateRWLockOwnerIterator` aby upewnić się, że jego implementacja wątków będzie zsynchronizowana.</span><span class="sxs-lookup"><span data-stu-id="70ef1-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70ef1-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70ef1-126">Requirements</span></span>  
 <span data-ttu-id="70ef1-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70ef1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70ef1-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70ef1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70ef1-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70ef1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70ef1-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70ef1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ef1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70ef1-131">See also</span></span>
- [<span data-ttu-id="70ef1-132">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="70ef1-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="70ef1-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="70ef1-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
