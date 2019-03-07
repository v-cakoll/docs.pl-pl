---
title: IHostThreadPoolManager::GetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8758bd416b721a95f48b8c8edb933cf617e13455
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466504"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="aa9be-102">IHostThreadPoolManager::GetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa9be-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="aa9be-103">Pobiera maksymalną liczbę wątków, które przechowuje hosta jednocześnie w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="aa9be-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa9be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa9be-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa9be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa9be-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="aa9be-106">[out] Wskaźnik do maksymalną liczbę wątków, które host przechowuje w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="aa9be-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa9be-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa9be-107">Return Value</span></span>  
  
|<span data-ttu-id="aa9be-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa9be-108">HRESULT</span></span>|<span data-ttu-id="aa9be-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aa9be-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa9be-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa9be-110">S_OK</span></span>|<span data-ttu-id="aa9be-111">`GetMaxThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="aa9be-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="aa9be-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa9be-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa9be-113">Środowisko uruchomieniowe języka wspólnego (CLR (nie został załadowany do procesu lub środowiska CLR jest w stanie, w której nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa9be-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa9be-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa9be-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa9be-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="aa9be-115">The call timed out.</span></span>|  
|<span data-ttu-id="aa9be-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa9be-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa9be-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="aa9be-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa9be-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa9be-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa9be-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="aa9be-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa9be-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa9be-120">E_FAIL</span></span>|<span data-ttu-id="aa9be-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aa9be-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa9be-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aa9be-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa9be-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa9be-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa9be-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="aa9be-124">E_NOTIMPL</span></span>|<span data-ttu-id="aa9be-125">Host nie zawiera implementacji `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="aa9be-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa9be-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa9be-126">Remarks</span></span>  
 <span data-ttu-id="aa9be-127">CLR wywołuje `GetMaxThreads` ustalenie, łączna liczba wątków w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="aa9be-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="aa9be-128">[Getavailablethreads —](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) metoda pobiera liczbę wątków, które nie są obecnie przetwarza elementy robocze.</span><span class="sxs-lookup"><span data-stu-id="aa9be-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="aa9be-129">Wszystkie żądania nad wartością zwróconą `pdwMaxWorkerThreads` parametru pozostają w kolejce do momentu wątków stają się dostępne.</span><span class="sxs-lookup"><span data-stu-id="aa9be-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="aa9be-130">Jeśli host nie dostarcza implementację `GetMaxThreads`, powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="aa9be-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa9be-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa9be-131">Requirements</span></span>  
 <span data-ttu-id="aa9be-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa9be-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa9be-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa9be-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa9be-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa9be-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa9be-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa9be-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9be-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa9be-136">See also</span></span>
- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="aa9be-137">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="aa9be-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="aa9be-138">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="aa9be-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="aa9be-139">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa9be-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
