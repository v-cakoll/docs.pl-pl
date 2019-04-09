---
title: IHostIoCompletionManager::GetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8875fb24512ddfea57d5f9249e58de3c12b8c507
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119167"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="48bd8-102">IHostIoCompletionManager::GetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="48bd8-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="48bd8-103">Pobiera maksymalną liczbę wątków, które można przyznać hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="48bd8-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48bd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48bd8-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48bd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48bd8-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="48bd8-106">[out] Wskaźnik do maksymalną liczbę wątków w puli wątków, które hosta można przyznać do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="48bd8-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48bd8-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="48bd8-107">Return Value</span></span>  
  
|<span data-ttu-id="48bd8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48bd8-108">HRESULT</span></span>|<span data-ttu-id="48bd8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="48bd8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48bd8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="48bd8-110">S_OK</span></span>|`GetMaxThreads` <span data-ttu-id="48bd8-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="48bd8-111">returned successfully.</span></span>|  
|<span data-ttu-id="48bd8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48bd8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48bd8-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="48bd8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48bd8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48bd8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48bd8-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="48bd8-115">The call timed out.</span></span>|  
|<span data-ttu-id="48bd8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48bd8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48bd8-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="48bd8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48bd8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48bd8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48bd8-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="48bd8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48bd8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48bd8-120">E_FAIL</span></span>|<span data-ttu-id="48bd8-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="48bd8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48bd8-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="48bd8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48bd8-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="48bd8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="48bd8-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="48bd8-124">E_NOTIMPL</span></span>|<span data-ttu-id="48bd8-125">Host nie zawiera implementacji `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="48bd8-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48bd8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48bd8-126">Remarks</span></span>  
 <span data-ttu-id="48bd8-127">Host może być wyłączną kontrolę nad liczbę wątków, które może być przydzielona do przetwarzania żądań We/Wy, powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="48bd8-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="48bd8-128">Z tego powodu host nie jest wymagane do zaimplementowania `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="48bd8-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="48bd8-129">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="48bd8-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48bd8-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48bd8-130">Requirements</span></span>  
 <span data-ttu-id="48bd8-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48bd8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48bd8-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48bd8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48bd8-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48bd8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="48bd8-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="48bd8-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="48bd8-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48bd8-135">See also</span></span>

- [<span data-ttu-id="48bd8-136">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="48bd8-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="48bd8-137">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="48bd8-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
