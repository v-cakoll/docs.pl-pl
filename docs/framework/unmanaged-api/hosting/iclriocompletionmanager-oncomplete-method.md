---
title: ICLRIoCompletionManager::OnComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d428bfc6816219669f47652e2fc182329d3f31d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503629"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="e3f29-102">ICLRIoCompletionManager::OnComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3f29-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="e3f29-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) stanu żądania We/Wy, który został wykonany przy użyciu wywołania [ihostiocompletionmanager::BIND —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e3f29-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3f29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3f29-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3f29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3f29-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="e3f29-106">[in] Wartość HRESULT, która wskazuje stan operacji wiązania.</span><span class="sxs-lookup"><span data-stu-id="e3f29-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
-   <span data-ttu-id="e3f29-107">S_OK wskazuje, że operacja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e3f29-107">S_OK indicates that the operation completed successfully.</span></span>  
  
-   <span data-ttu-id="e3f29-108">HOST_E_INTERRUPTED wskazuje, że wywołanie zakończone przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="e3f29-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
-   <span data-ttu-id="e3f29-109">E_FAIL wskazuje, że wystąpił nieznany, nieodwracalny, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="e3f29-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="e3f29-110">[in] Liczba bajtów przesłanych podczas przetwarzania żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="e3f29-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="e3f29-111">[in] Wskaźnik do `OVERLAPPED` strukturę, która została przekazana do wywołania `IHostIoCompletionManager::Bind` metody.</span><span class="sxs-lookup"><span data-stu-id="e3f29-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3f29-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3f29-112">Return Value</span></span>  
  
|<span data-ttu-id="e3f29-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3f29-113">HRESULT</span></span>|<span data-ttu-id="e3f29-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e3f29-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3f29-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3f29-115">S_OK</span></span>|<span data-ttu-id="e3f29-116">`OnComplete` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e3f29-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="e3f29-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3f29-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3f29-118">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e3f29-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e3f29-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e3f29-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e3f29-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e3f29-120">The call timed out.</span></span>|  
|<span data-ttu-id="e3f29-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3f29-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e3f29-122">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e3f29-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e3f29-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e3f29-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e3f29-124">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e3f29-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e3f29-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3f29-125">E_FAIL</span></span>|<span data-ttu-id="e3f29-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e3f29-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e3f29-127">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e3f29-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e3f29-128">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e3f29-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3f29-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3f29-129">Remarks</span></span>  
 <span data-ttu-id="e3f29-130">Jeśli host implementuje abstrakcję zakończenia operacji We/Wy, środowisko CLR sprawia, że żądania We/Wy za pośrednictwem hosta przy użyciu metody [ihostiocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e3f29-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="e3f29-131">Host następnie wywołuje `OnComplete` metodę, aby powiadomić środowiska uruchomieniowego wyniki takich żądań.</span><span class="sxs-lookup"><span data-stu-id="e3f29-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3f29-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3f29-132">Requirements</span></span>  
 <span data-ttu-id="e3f29-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3f29-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3f29-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3f29-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3f29-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3f29-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3f29-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3f29-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f29-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3f29-137">See also</span></span>
- [<span data-ttu-id="e3f29-138">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3f29-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e3f29-139">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3f29-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="e3f29-140">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3f29-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
