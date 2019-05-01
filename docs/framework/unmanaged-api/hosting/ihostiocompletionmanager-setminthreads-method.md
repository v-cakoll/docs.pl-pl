---
title: IHostIoCompletionManager::SetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fd37546c63ef5e5f25686e105247555dfeb132a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796750"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="9117d-102">IHostIoCompletionManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="9117d-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="9117d-103">Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="9117d-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9117d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9117d-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9117d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9117d-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="9117d-106">[in] Minimalna liczba wątków zakończenia operacji We/Wy, które należy utworzyć hosta.</span><span class="sxs-lookup"><span data-stu-id="9117d-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9117d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9117d-107">Return Value</span></span>  
  
|<span data-ttu-id="9117d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9117d-108">HRESULT</span></span>|<span data-ttu-id="9117d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9117d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9117d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9117d-110">S_OK</span></span>|<span data-ttu-id="9117d-111">`SetMinThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="9117d-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9117d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9117d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9117d-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9117d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9117d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9117d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9117d-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="9117d-115">The call timed out.</span></span>|  
|<span data-ttu-id="9117d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9117d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9117d-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="9117d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9117d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9117d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9117d-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="9117d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9117d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9117d-120">E_FAIL</span></span>|<span data-ttu-id="9117d-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9117d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9117d-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="9117d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9117d-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9117d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9117d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9117d-124">E_NOTIMPL</span></span>|<span data-ttu-id="9117d-125">Host nie zawiera implementacji `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="9117d-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9117d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9117d-126">Remarks</span></span>  
 <span data-ttu-id="9117d-127">Host może być wyłączną kontrolę nad liczbę wątków, które może być przydzielona do przetwarzania żądań We/Wy, powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="9117d-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="9117d-128">Z tego powodu host nie jest wymagane do zaimplementowania `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="9117d-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="9117d-129">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="9117d-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9117d-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9117d-130">Requirements</span></span>  
 <span data-ttu-id="9117d-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9117d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9117d-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9117d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9117d-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9117d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9117d-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9117d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9117d-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9117d-135">See also</span></span>

- [<span data-ttu-id="9117d-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9117d-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="9117d-137">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="9117d-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="9117d-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9117d-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
