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
ms.openlocfilehash: efbfa310c90f48c99219cb185f090a1b854949a2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842286"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="037a7-102">IHostThreadPoolManager::GetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="037a7-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="037a7-103">Pobiera maksymalną liczbę wątków, które Host przechowuje współbieżnie w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="037a7-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="037a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="037a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="037a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="037a7-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="037a7-106">określoną Wskaźnik do maksymalnej liczby wątków, które Host przechowuje w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="037a7-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="037a7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="037a7-107">Return Value</span></span>  
  
|<span data-ttu-id="037a7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="037a7-108">HRESULT</span></span>|<span data-ttu-id="037a7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="037a7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="037a7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="037a7-110">S_OK</span></span>|<span data-ttu-id="037a7-111">`GetMaxThreads`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="037a7-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="037a7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="037a7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="037a7-113">Środowisko uruchomieniowe języka wspólnego (CLR (nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="037a7-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="037a7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="037a7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="037a7-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="037a7-115">The call timed out.</span></span>|  
|<span data-ttu-id="037a7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="037a7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="037a7-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="037a7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="037a7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="037a7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="037a7-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="037a7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="037a7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="037a7-120">E_FAIL</span></span>|<span data-ttu-id="037a7-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="037a7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="037a7-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="037a7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="037a7-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="037a7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="037a7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="037a7-124">E_NOTIMPL</span></span>|<span data-ttu-id="037a7-125">Host nie oferuje implementacji programu `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="037a7-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="037a7-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="037a7-126">Remarks</span></span>  
 <span data-ttu-id="037a7-127">CLR wywołuje, `GetMaxThreads` Aby określić łączną liczbę wątków w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="037a7-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="037a7-128">Metoda [GetAvailableThreads —](ihostthreadpoolmanager-getavailablethreads-method.md) Pobiera liczbę wątków, które aktualnie nie przetwarzają elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="037a7-128">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="037a7-129">Wszystkie żądania powyżej zwracanej wartości `pdwMaxWorkerThreads` parametru pozostają w kolejce, dopóki wątki staną się niedostępne.</span><span class="sxs-lookup"><span data-stu-id="037a7-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="037a7-130">Jeśli host nie dostarcza implementacji `GetMaxThreads` , powinien zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="037a7-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="037a7-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="037a7-131">Requirements</span></span>  
 <span data-ttu-id="037a7-132">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="037a7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="037a7-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="037a7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="037a7-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="037a7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="037a7-135">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="037a7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="037a7-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="037a7-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="037a7-137">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="037a7-137">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="037a7-138">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="037a7-138">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="037a7-139">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="037a7-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
