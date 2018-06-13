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
ms.openlocfilehash: fa6e0e2447cc3ff6766bb33bb603388f37ec3ce0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443774"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="655df-102">IHostThreadPoolManager::GetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="655df-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="655df-103">Pobiera maksymalną liczbę wątków, która jest obsługiwana przez hosta jednocześnie w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="655df-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="655df-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="655df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="655df-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="655df-106">[out] Wskaźnik do maksymalną liczbę wątków, która jest obsługiwana przez hosta w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="655df-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="655df-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="655df-107">Return Value</span></span>  
  
|<span data-ttu-id="655df-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="655df-108">HRESULT</span></span>|<span data-ttu-id="655df-109">Opis</span><span class="sxs-lookup"><span data-stu-id="655df-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="655df-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="655df-110">S_OK</span></span>|<span data-ttu-id="655df-111">`GetMaxThreads` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="655df-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="655df-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="655df-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="655df-113">Środowisko uruchomieniowe języka wspólnego (CLR (nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kodu zarządzanego lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="655df-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="655df-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="655df-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="655df-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="655df-115">The call timed out.</span></span>|  
|<span data-ttu-id="655df-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="655df-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="655df-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="655df-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="655df-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="655df-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="655df-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="655df-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="655df-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="655df-120">E_FAIL</span></span>|<span data-ttu-id="655df-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="655df-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="655df-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="655df-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="655df-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="655df-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="655df-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="655df-124">E_NOTIMPL</span></span>|<span data-ttu-id="655df-125">Host nie zapewniać implementację elementu `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="655df-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655df-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="655df-126">Remarks</span></span>  
 <span data-ttu-id="655df-127">Wywołania CLR `GetMaxThreads` ustalenie łączna liczba wątków w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="655df-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="655df-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) metoda pobiera liczbę wątków, które nie są aktualnie przetwarza elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="655df-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="655df-129">Wszystkie żądania powyżej wartość `pdwMaxWorkerThreads` parametru pozostają w kolejce do momentu wątków staną się dostępne.</span><span class="sxs-lookup"><span data-stu-id="655df-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="655df-130">Jeśli host nie zapewniać implementację elementu `GetMaxThreads`, powinien on zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="655df-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="655df-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="655df-131">Requirements</span></span>  
 <span data-ttu-id="655df-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="655df-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="655df-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="655df-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="655df-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="655df-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="655df-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="655df-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655df-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="655df-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="655df-137">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="655df-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="655df-138">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="655df-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="655df-139">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="655df-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
