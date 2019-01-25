---
title: IHostThreadPoolManager::SetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 905ce9183d295568977eb7e216e5327d6b4ee8bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636095"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="e4d2a-102">IHostThreadPoolManager::SetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4d2a-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="e4d2a-103">Ustawia maksymalną liczbę wątków, zapewniające przez hosta w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4d2a-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4d2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4d2a-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="e4d2a-106">Maksymalna liczba wątków w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4d2a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e4d2a-107">Return Value</span></span>  
  
|<span data-ttu-id="e4d2a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4d2a-108">HRESULT</span></span>|<span data-ttu-id="e4d2a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e4d2a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4d2a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4d2a-110">S_OK</span></span>|<span data-ttu-id="e4d2a-111">`SetMaxThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e4d2a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4d2a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4d2a-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4d2a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4d2a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4d2a-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-115">The call timed out.</span></span>|  
|<span data-ttu-id="e4d2a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4d2a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4d2a-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4d2a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4d2a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4d2a-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4d2a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4d2a-120">E_FAIL</span></span>|<span data-ttu-id="e4d2a-121">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e4d2a-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4d2a-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e4d2a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e4d2a-124">E_NOTIMPL</span></span>|<span data-ttu-id="e4d2a-125">Host nie zawiera implementacji `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4d2a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4d2a-126">Remarks</span></span>  
 <span data-ttu-id="e4d2a-127">Host nie jest wymagany w celu umożliwienia CLR skonfigurować rozmiar puli wątków.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="e4d2a-128">Niektóre hosty może być wyłączną kontrolę nad puli wątków powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e4d2a-129">W tym przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="e4d2a-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d2a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4d2a-130">Requirements</span></span>  
 <span data-ttu-id="e4d2a-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4d2a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4d2a-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4d2a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4d2a-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4d2a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4d2a-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d2a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d2a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4d2a-135">See also</span></span>
- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="e4d2a-136">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="e4d2a-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="e4d2a-137">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="e4d2a-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="e4d2a-138">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4d2a-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
