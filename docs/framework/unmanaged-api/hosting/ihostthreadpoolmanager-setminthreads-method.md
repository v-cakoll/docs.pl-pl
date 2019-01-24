---
title: IHostThreadPoolManager::SetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d0e8198fece4a718b6478f199820738d49ed988
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519843"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="5013f-102">IHostThreadPoolManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="5013f-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="5013f-103">Ustawia minimalna liczba bezczynnych wątków, które hosta, musisz utrzymywać w oczekiwaniu żądań.</span><span class="sxs-lookup"><span data-stu-id="5013f-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5013f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5013f-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5013f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5013f-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="5013f-106">[in] Nowe minimalna liczba wątków, które należy zachować hosta.</span><span class="sxs-lookup"><span data-stu-id="5013f-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5013f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5013f-107">Return Value</span></span>  
  
|<span data-ttu-id="5013f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5013f-108">HRESULT</span></span>|<span data-ttu-id="5013f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5013f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5013f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5013f-110">S_OK</span></span>|<span data-ttu-id="5013f-111">`SetMinThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5013f-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5013f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5013f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5013f-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="5013f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5013f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5013f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5013f-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="5013f-115">The call timed out.</span></span>|  
|<span data-ttu-id="5013f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5013f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5013f-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="5013f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5013f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5013f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5013f-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="5013f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5013f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5013f-120">E_FAIL</span></span>|<span data-ttu-id="5013f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5013f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5013f-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="5013f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5013f-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5013f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5013f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5013f-124">E_NOTIMPL</span></span>|<span data-ttu-id="5013f-125">Host nie zawiera implementacji `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5013f-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5013f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5013f-126">Remarks</span></span>  
 <span data-ttu-id="5013f-127">Host nie musi dostarczać implementację `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5013f-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="5013f-128">W tym przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="5013f-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5013f-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5013f-129">Requirements</span></span>  
 <span data-ttu-id="5013f-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5013f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5013f-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5013f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5013f-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5013f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5013f-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5013f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5013f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5013f-134">See also</span></span>
- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="5013f-135">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5013f-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="5013f-136">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="5013f-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="5013f-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5013f-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
