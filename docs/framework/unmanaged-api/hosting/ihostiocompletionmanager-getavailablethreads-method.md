---
title: IHostIoCompletionManager::GetAvailableThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 2fa429979faa04518397cf58aaa62d3e45230a76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133834"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="a1674-102">IHostIoCompletionManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1674-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="a1674-103">Pobiera liczbę wątków zakończenia operacji we/wy (całkowitej liczby wątków zarządzanych przez hosta), które nie obsługują obecnie żądań.</span><span class="sxs-lookup"><span data-stu-id="a1674-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1674-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1674-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1674-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1674-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="a1674-106">określoną Wskaźnik do liczby wątków zakończenia we/wy zarządzanych przez hosta, które są obecnie dostępne dla żądań obsługi.</span><span class="sxs-lookup"><span data-stu-id="a1674-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1674-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1674-107">Return Value</span></span>  
  
|<span data-ttu-id="a1674-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1674-108">HRESULT</span></span>|<span data-ttu-id="a1674-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a1674-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1674-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1674-110">S_OK</span></span>|<span data-ttu-id="a1674-111">`GetAvailableThreads` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a1674-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="a1674-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1674-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1674-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a1674-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1674-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1674-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1674-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a1674-115">The call timed out.</span></span>|  
|<span data-ttu-id="a1674-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1674-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1674-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a1674-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1674-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1674-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1674-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a1674-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1674-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1674-120">E_FAIL</span></span>|<span data-ttu-id="a1674-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a1674-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1674-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a1674-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1674-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a1674-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a1674-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a1674-124">E_NOTIMPL</span></span>|<span data-ttu-id="a1674-125">Host nie dostarcza implementacji `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="a1674-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1674-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1674-126">Remarks</span></span>  
 <span data-ttu-id="a1674-127">Host może potrzebować wyłącznej kontroli nad rozmiarem puli wątków ukończenia we/wy, z przyczyn takich jak implementacja, wydajność lub skalowalność.</span><span class="sxs-lookup"><span data-stu-id="a1674-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="a1674-128">W związku z tym host nie jest wymagany do implementowania `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="a1674-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="a1674-129">W takim przypadku host powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="a1674-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1674-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1674-130">Requirements</span></span>  
 <span data-ttu-id="a1674-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1674-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1674-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1674-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1674-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1674-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1674-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1674-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1674-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1674-135">See also</span></span>

- [<span data-ttu-id="a1674-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1674-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a1674-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1674-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
