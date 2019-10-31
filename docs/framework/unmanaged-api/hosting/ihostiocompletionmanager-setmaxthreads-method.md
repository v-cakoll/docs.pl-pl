---
title: IHostIoCompletionManager::SetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 7a16c141d9d07af82bd984955e06199e66ce3bbf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133766"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="7f502-102">IHostIoCompletionManager::SetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f502-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="7f502-103">Ustawia maksymalną liczbę wątków przynoszących Host do obsługi żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="7f502-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f502-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f502-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f502-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f502-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="7f502-106">podczas Maksymalna liczba wątków do przydzielenia dla żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="7f502-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f502-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7f502-107">Return Value</span></span>  
  
|<span data-ttu-id="7f502-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f502-108">HRESULT</span></span>|<span data-ttu-id="7f502-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7f502-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f502-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f502-110">S_OK</span></span>|<span data-ttu-id="7f502-111">`SetMaxThreads` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7f502-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="7f502-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f502-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f502-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7f502-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f502-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f502-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f502-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="7f502-115">The call timed out.</span></span>|  
|<span data-ttu-id="7f502-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f502-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f502-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7f502-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f502-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f502-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f502-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="7f502-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f502-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f502-120">E_FAIL</span></span>|<span data-ttu-id="7f502-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7f502-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f502-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="7f502-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f502-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f502-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7f502-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="7f502-124">E_NOTIMPL</span></span>|<span data-ttu-id="7f502-125">Host nie dostarcza implementacji `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="7f502-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f502-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f502-126">Remarks</span></span>  
 <span data-ttu-id="7f502-127">`SetMaxThreads` zapewnia środowisko CLR z możliwością ustawienia maksymalnej liczby wątków dostępnych do obsługi żądań w portach we/wy.</span><span class="sxs-lookup"><span data-stu-id="7f502-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="7f502-128">Host może potrzebować wyłącznej kontroli nad rozmiarem puli wątków, z przyczyn takich jak implementacja, wydajność lub skalowalność.</span><span class="sxs-lookup"><span data-stu-id="7f502-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="7f502-129">Z tego powodu host nie musi implementować `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="7f502-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="7f502-130">W takim przypadku host powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="7f502-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f502-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f502-131">Requirements</span></span>  
 <span data-ttu-id="7f502-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f502-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f502-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f502-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f502-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7f502-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f502-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f502-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f502-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f502-136">See also</span></span>

- [<span data-ttu-id="7f502-137">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f502-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="7f502-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f502-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
