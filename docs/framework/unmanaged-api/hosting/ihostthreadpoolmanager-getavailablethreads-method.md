---
title: IHostThreadPoolManager::GetAvailableThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: 21449d9365e6260267d3c79f384f6136ce894821
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122096"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="2e09f-102">IHostThreadPoolManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e09f-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="2e09f-103">Pobiera liczbę wątków w puli wątków, które nie przetwarzają obecnie elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="2e09f-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e09f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e09f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e09f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e09f-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="2e09f-106">określoną Wskaźnik do liczby wątków w puli wątków, które nie przetwarzają obecnie elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="2e09f-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e09f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2e09f-107">Return Value</span></span>  
  
|<span data-ttu-id="2e09f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e09f-108">HRESULT</span></span>|<span data-ttu-id="2e09f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2e09f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e09f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e09f-110">S_OK</span></span>|<span data-ttu-id="2e09f-111">`GetAvailableThreads` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="2e09f-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2e09f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e09f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e09f-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2e09f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e09f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e09f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e09f-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2e09f-115">The call timed out.</span></span>|  
|<span data-ttu-id="2e09f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e09f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e09f-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2e09f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e09f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e09f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e09f-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2e09f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e09f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e09f-120">E_FAIL</span></span>|<span data-ttu-id="2e09f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2e09f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e09f-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="2e09f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e09f-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2e09f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2e09f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2e09f-124">E_NOTIMPL</span></span>|<span data-ttu-id="2e09f-125">Host nie dostarcza implementacji `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="2e09f-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e09f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e09f-126">Remarks</span></span>  
 <span data-ttu-id="2e09f-127">Jeśli host nie dostarcza implementacji `GetAvailableThreads`, powinien zwrócić wartość HRESULT równą E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2e09f-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e09f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e09f-128">Requirements</span></span>  
 <span data-ttu-id="2e09f-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e09f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e09f-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e09f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e09f-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e09f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e09f-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e09f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e09f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e09f-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="2e09f-134">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e09f-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
