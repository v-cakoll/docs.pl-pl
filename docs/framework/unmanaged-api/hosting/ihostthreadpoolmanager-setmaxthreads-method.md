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
ms.openlocfilehash: 442e4566749aade5a7f8164fcc43baad902928c0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749115"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="37fa6-102">IHostThreadPoolManager::SetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="37fa6-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="37fa6-103">Ustawia maksymalną liczbę wątków, zapewniające przez hosta w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="37fa6-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fa6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37fa6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37fa6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37fa6-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="37fa6-106">Maksymalna liczba wątków w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="37fa6-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37fa6-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37fa6-107">Return Value</span></span>  
  
|<span data-ttu-id="37fa6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37fa6-108">HRESULT</span></span>|<span data-ttu-id="37fa6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="37fa6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37fa6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="37fa6-110">S_OK</span></span>|<span data-ttu-id="37fa6-111">`SetMaxThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="37fa6-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="37fa6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37fa6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37fa6-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="37fa6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37fa6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37fa6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37fa6-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="37fa6-115">The call timed out.</span></span>|  
|<span data-ttu-id="37fa6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37fa6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37fa6-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="37fa6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37fa6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37fa6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37fa6-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="37fa6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37fa6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37fa6-120">E_FAIL</span></span>|<span data-ttu-id="37fa6-121">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="37fa6-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="37fa6-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="37fa6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37fa6-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37fa6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="37fa6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="37fa6-124">E_NOTIMPL</span></span>|<span data-ttu-id="37fa6-125">Host nie zawiera implementacji `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="37fa6-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37fa6-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37fa6-126">Remarks</span></span>  
 <span data-ttu-id="37fa6-127">Host nie jest wymagany w celu umożliwienia CLR skonfigurować rozmiar puli wątków.</span><span class="sxs-lookup"><span data-stu-id="37fa6-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="37fa6-128">Niektóre hosty może być wyłączną kontrolę nad puli wątków powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="37fa6-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="37fa6-129">W tym przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="37fa6-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37fa6-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37fa6-130">Requirements</span></span>  
 <span data-ttu-id="37fa6-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37fa6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37fa6-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37fa6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37fa6-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37fa6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37fa6-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37fa6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fa6-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37fa6-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="37fa6-136">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="37fa6-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="37fa6-137">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="37fa6-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="37fa6-138">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="37fa6-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
