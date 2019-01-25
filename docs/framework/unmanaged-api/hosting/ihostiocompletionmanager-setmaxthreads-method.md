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
ms.openlocfilehash: 51ea342b59bc328a5c8e187dc55b68a8e8e8a7c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657392"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="a6dd9-102">IHostIoCompletionManager::SetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6dd9-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="a6dd9-103">Ustawia maksymalną liczbę wątków, które spowoduje przyznanie hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6dd9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6dd9-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6dd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6dd9-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="a6dd9-106">[in] Maksymalna liczba wątków, aby przyznać dla żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6dd9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a6dd9-107">Return Value</span></span>  
  
|<span data-ttu-id="a6dd9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6dd9-108">HRESULT</span></span>|<span data-ttu-id="a6dd9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a6dd9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6dd9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6dd9-110">S_OK</span></span>|<span data-ttu-id="a6dd9-111">`SetMaxThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="a6dd9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6dd9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6dd9-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6dd9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6dd9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6dd9-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-115">The call timed out.</span></span>|  
|<span data-ttu-id="a6dd9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6dd9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6dd9-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6dd9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6dd9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6dd9-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6dd9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6dd9-120">E_FAIL</span></span>|<span data-ttu-id="a6dd9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6dd9-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6dd9-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a6dd9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a6dd9-124">E_NOTIMPL</span></span>|<span data-ttu-id="a6dd9-125">Host nie zawiera implementacji `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6dd9-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6dd9-126">Remarks</span></span>  
 <span data-ttu-id="a6dd9-127">`SetMaxThreads` zawiera środowisko CLR z szansą sprzedaży, aby ustawić maksymalną liczbę wątków, które są dostępne do obsługi żądań na portów We/Wy.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="a6dd9-128">Host może być konieczne wyłączną kontrolę nad rozmiar puli wątków powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="a6dd9-129">Z tego powodu host nie jest wymagane do zaimplementowania `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="a6dd9-130">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="a6dd9-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6dd9-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6dd9-131">Requirements</span></span>  
 <span data-ttu-id="a6dd9-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6dd9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6dd9-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6dd9-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6dd9-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6dd9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6dd9-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6dd9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6dd9-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6dd9-136">See also</span></span>
- [<span data-ttu-id="a6dd9-137">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6dd9-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a6dd9-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6dd9-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
