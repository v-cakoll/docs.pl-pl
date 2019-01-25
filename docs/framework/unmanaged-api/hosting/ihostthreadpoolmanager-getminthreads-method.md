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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8010ac602c82c7da2af9d0678227a6ce1c91391a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521468"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="4a72e-102">IHostThreadPoolManager::GetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a72e-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="4a72e-103">Pobiera minimalna liczba bezczynnych wątków, które przechowuje hosta w puli wątków, oczekując na żądania.</span><span class="sxs-lookup"><span data-stu-id="4a72e-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a72e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a72e-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a72e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a72e-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="4a72e-106">[out] Wskaźnik do minimalna liczba bezczynnych wątków, które obecnie obsługuje hosta.</span><span class="sxs-lookup"><span data-stu-id="4a72e-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a72e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4a72e-107">Return Value</span></span>  
  
|<span data-ttu-id="4a72e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a72e-108">HRESULT</span></span>|<span data-ttu-id="4a72e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4a72e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a72e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a72e-110">S_OK</span></span>|<span data-ttu-id="4a72e-111">`GetMinThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4a72e-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4a72e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a72e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a72e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="4a72e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a72e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a72e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a72e-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="4a72e-115">The call timed out.</span></span>|  
|<span data-ttu-id="4a72e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a72e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a72e-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="4a72e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a72e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a72e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a72e-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="4a72e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a72e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a72e-120">E_FAIL</span></span>|<span data-ttu-id="4a72e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4a72e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a72e-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4a72e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a72e-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a72e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a72e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4a72e-124">E_NOTIMPL</span></span>|<span data-ttu-id="4a72e-125">Host nie zawiera implementacji `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4a72e-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a72e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a72e-126">Remarks</span></span>  
 <span data-ttu-id="4a72e-127">Host nie musi dostarczać implementację `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4a72e-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="4a72e-128">W tym przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4a72e-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a72e-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a72e-129">Requirements</span></span>  
 <span data-ttu-id="4a72e-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a72e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a72e-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a72e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a72e-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a72e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a72e-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a72e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a72e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a72e-134">See also</span></span>
- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4a72e-135">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="4a72e-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="4a72e-136">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="4a72e-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="4a72e-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a72e-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
