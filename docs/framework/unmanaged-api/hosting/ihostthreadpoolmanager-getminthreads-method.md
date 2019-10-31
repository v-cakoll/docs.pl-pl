---
title: IHostThreadPoolManager::GetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: ce1abb75c5135a9bb23f1ad2d2acbd40d9111b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122065"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="f3ee5-102">IHostThreadPoolManager::GetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3ee5-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="f3ee5-103">Pobiera minimalną liczbę bezczynnych wątków, które Host przechowuje w puli wątków w oczekiwaniu na żądania.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ee5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3ee5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3ee5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3ee5-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="f3ee5-106">określoną Wskaźnik do minimalnej liczby bezczynnych wątków roboczych, które aktualnie przechowuje host.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3ee5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f3ee5-107">Return Value</span></span>  
  
|<span data-ttu-id="f3ee5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3ee5-108">HRESULT</span></span>|<span data-ttu-id="f3ee5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f3ee5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3ee5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3ee5-110">S_OK</span></span>|<span data-ttu-id="f3ee5-111">`GetMinThreads` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f3ee5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f3ee5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f3ee5-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f3ee5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3ee5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f3ee5-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-115">The call timed out.</span></span>|  
|<span data-ttu-id="f3ee5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3ee5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f3ee5-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f3ee5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f3ee5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f3ee5-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f3ee5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f3ee5-120">E_FAIL</span></span>|<span data-ttu-id="f3ee5-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f3ee5-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f3ee5-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f3ee5-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f3ee5-124">E_NOTIMPL</span></span>|<span data-ttu-id="f3ee5-125">Host nie dostarcza implementacji `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3ee5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3ee5-126">Remarks</span></span>  
 <span data-ttu-id="f3ee5-127">Host nie jest wymagany do zapewnienia implementacji `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="f3ee5-128">W takim przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f3ee5-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3ee5-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3ee5-129">Requirements</span></span>  
 <span data-ttu-id="f3ee5-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3ee5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ee5-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3ee5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3ee5-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3ee5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3ee5-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ee5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ee5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3ee5-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="f3ee5-135">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="f3ee5-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="f3ee5-136">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="f3ee5-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="f3ee5-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3ee5-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
