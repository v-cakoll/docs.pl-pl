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
ms.openlocfilehash: 8b1fc936b601d327ce6306f22dbec2c1078718da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133731"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="e93e0-102">IHostIoCompletionManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="e93e0-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="e93e0-103">Ustawia minimalną liczbę wątków, które host powinien przydzielić do zakończenia operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="e93e0-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e93e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e93e0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e93e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e93e0-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="e93e0-106">podczas Minimalna liczba wątków zakończenia we/wy, które powinien utworzyć host.</span><span class="sxs-lookup"><span data-stu-id="e93e0-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e93e0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e93e0-107">Return Value</span></span>  
  
|<span data-ttu-id="e93e0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e93e0-108">HRESULT</span></span>|<span data-ttu-id="e93e0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e93e0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e93e0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e93e0-110">S_OK</span></span>|<span data-ttu-id="e93e0-111">`SetMinThreads` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e93e0-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e93e0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e93e0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e93e0-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e93e0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e93e0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e93e0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e93e0-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e93e0-115">The call timed out.</span></span>|  
|<span data-ttu-id="e93e0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e93e0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e93e0-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e93e0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e93e0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e93e0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e93e0-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="e93e0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e93e0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e93e0-120">E_FAIL</span></span>|<span data-ttu-id="e93e0-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e93e0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e93e0-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="e93e0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e93e0-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e93e0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e93e0-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e93e0-124">E_NOTIMPL</span></span>|<span data-ttu-id="e93e0-125">Host nie dostarcza implementacji `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="e93e0-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e93e0-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e93e0-126">Remarks</span></span>  
 <span data-ttu-id="e93e0-127">Host może potrzebować wyłącznej kontroli nad liczbą wątków, które mogą być przydzielone do przetwarzania żądań we/wy, z przyczyn takich jak implementacja, wydajność lub skalowalność.</span><span class="sxs-lookup"><span data-stu-id="e93e0-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e93e0-128">Z tego powodu host nie musi implementować `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="e93e0-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="e93e0-129">W takim przypadku host powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="e93e0-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e93e0-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e93e0-130">Requirements</span></span>  
 <span data-ttu-id="e93e0-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e93e0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e93e0-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e93e0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e93e0-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e93e0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e93e0-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e93e0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93e0-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e93e0-135">See also</span></span>

- [<span data-ttu-id="e93e0-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e93e0-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e93e0-137">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="e93e0-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="e93e0-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e93e0-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
