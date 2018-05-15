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
ms.openlocfilehash: 3f978f565dd93eb10a68942fc463f7d5cc212e6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="41f88-102">IHostThreadPoolManager::SetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="41f88-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="41f88-103">Ustawia maksymalną liczbę wątków, które host może przechowywać w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="41f88-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41f88-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41f88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41f88-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="41f88-106">Maksymalna liczba wątków roboczych w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="41f88-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41f88-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="41f88-107">Return Value</span></span>  
  
|<span data-ttu-id="41f88-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41f88-108">HRESULT</span></span>|<span data-ttu-id="41f88-109">Opis</span><span class="sxs-lookup"><span data-stu-id="41f88-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41f88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="41f88-110">S_OK</span></span>|<span data-ttu-id="41f88-111">`SetMaxThreads` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="41f88-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="41f88-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41f88-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41f88-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="41f88-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41f88-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41f88-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41f88-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="41f88-115">The call timed out.</span></span>|  
|<span data-ttu-id="41f88-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41f88-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41f88-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="41f88-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41f88-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41f88-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41f88-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="41f88-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41f88-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41f88-120">E_FAIL</span></span>|<span data-ttu-id="41f88-121">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="41f88-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="41f88-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="41f88-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41f88-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="41f88-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="41f88-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="41f88-124">E_NOTIMPL</span></span>|<span data-ttu-id="41f88-125">Host nie zapewniać implementację elementu `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="41f88-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41f88-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41f88-126">Remarks</span></span>  
 <span data-ttu-id="41f88-127">Host nie jest wymagana w celu dopuszczenia CLR skonfigurować rozmiar puli wątków.</span><span class="sxs-lookup"><span data-stu-id="41f88-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="41f88-128">Niektóre hosty, może być wyłączną kontrolę nad puli wątków powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="41f88-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="41f88-129">W takim przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="41f88-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41f88-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41f88-130">Requirements</span></span>  
 <span data-ttu-id="41f88-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41f88-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41f88-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41f88-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41f88-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41f88-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41f88-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41f88-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f88-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41f88-135">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="41f88-136">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="41f88-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="41f88-137">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="41f88-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="41f88-138">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="41f88-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
