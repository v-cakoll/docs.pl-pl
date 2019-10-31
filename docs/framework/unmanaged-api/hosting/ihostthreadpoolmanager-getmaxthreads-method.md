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
ms.openlocfilehash: e53265556de026e84af7ca345a5f82be3c5ff812
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122058"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="9d6f0-102">IHostThreadPoolManager::GetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d6f0-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="9d6f0-103">Pobiera maksymalną liczbę wątków, które Host przechowuje współbieżnie w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d6f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d6f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d6f0-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="9d6f0-106">określoną Wskaźnik do maksymalnej liczby wątków, które Host przechowuje w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d6f0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d6f0-107">Return Value</span></span>  
  
|<span data-ttu-id="9d6f0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d6f0-108">HRESULT</span></span>|<span data-ttu-id="9d6f0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9d6f0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d6f0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d6f0-110">S_OK</span></span>|<span data-ttu-id="9d6f0-111">`GetMaxThreads` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9d6f0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d6f0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d6f0-113">Środowisko uruchomieniowe języka wspólnego (CLR (nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d6f0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d6f0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d6f0-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-115">The call timed out.</span></span>|  
|<span data-ttu-id="9d6f0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d6f0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d6f0-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d6f0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d6f0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d6f0-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d6f0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d6f0-120">E_FAIL</span></span>|<span data-ttu-id="9d6f0-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d6f0-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d6f0-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d6f0-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9d6f0-124">E_NOTIMPL</span></span>|<span data-ttu-id="9d6f0-125">Host nie dostarcza implementacji `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d6f0-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d6f0-126">Remarks</span></span>  
 <span data-ttu-id="9d6f0-127">Wywołania CLR `GetMaxThreads`, aby określić łączną liczbę wątków w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="9d6f0-128">Metoda [GetAvailableThreads —](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) Pobiera liczbę wątków, które aktualnie nie przetwarzają elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="9d6f0-129">Wszystkie żądania powyżej zwróconej wartości parametru `pdwMaxWorkerThreads` pozostają w kolejce, dopóki wątki staną się niedostępne.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="9d6f0-130">Jeśli host nie dostarcza implementacji `GetMaxThreads`, powinien zwrócić wartość HRESULT równą E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="9d6f0-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6f0-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d6f0-131">Requirements</span></span>  
 <span data-ttu-id="9d6f0-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6f0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6f0-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d6f0-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d6f0-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d6f0-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d6f0-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6f0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6f0-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d6f0-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="9d6f0-137">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="9d6f0-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="9d6f0-138">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="9d6f0-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="9d6f0-139">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d6f0-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
