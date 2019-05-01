---
title: IHostIoCompletionManager::SetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 345c7b88b6967773a185538943591383a686748c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796763"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="34f7c-102">IHostIoCompletionManager::SetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="34f7c-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="34f7c-103">Ustawia maksymalną liczbę wątków, które spowoduje przyznanie hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="34f7c-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f7c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34f7c-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34f7c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34f7c-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="34f7c-106">[in] Maksymalna liczba wątków, aby przyznać dla żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="34f7c-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34f7c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34f7c-107">Return Value</span></span>  
  
|<span data-ttu-id="34f7c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34f7c-108">HRESULT</span></span>|<span data-ttu-id="34f7c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="34f7c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34f7c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="34f7c-110">S_OK</span></span>|<span data-ttu-id="34f7c-111">`SetMaxThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="34f7c-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="34f7c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34f7c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34f7c-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="34f7c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34f7c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34f7c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34f7c-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="34f7c-115">The call timed out.</span></span>|  
|<span data-ttu-id="34f7c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34f7c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34f7c-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="34f7c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34f7c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34f7c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34f7c-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="34f7c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34f7c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34f7c-120">E_FAIL</span></span>|<span data-ttu-id="34f7c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="34f7c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34f7c-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="34f7c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34f7c-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34f7c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="34f7c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="34f7c-124">E_NOTIMPL</span></span>|<span data-ttu-id="34f7c-125">Host nie zawiera implementacji `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="34f7c-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34f7c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34f7c-126">Remarks</span></span>  
 <span data-ttu-id="34f7c-127">`SetMaxThreads` zawiera środowisko CLR z szansą sprzedaży, aby ustawić maksymalną liczbę wątków, które są dostępne do obsługi żądań na portów We/Wy.</span><span class="sxs-lookup"><span data-stu-id="34f7c-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="34f7c-128">Host może być konieczne wyłączną kontrolę nad rozmiar puli wątków powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="34f7c-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="34f7c-129">Z tego powodu host nie jest wymagane do zaimplementowania `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="34f7c-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="34f7c-130">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="34f7c-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34f7c-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34f7c-131">Requirements</span></span>  
 <span data-ttu-id="34f7c-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34f7c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f7c-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34f7c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34f7c-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34f7c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34f7c-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34f7c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f7c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34f7c-136">See also</span></span>

- [<span data-ttu-id="34f7c-137">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="34f7c-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="34f7c-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="34f7c-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
