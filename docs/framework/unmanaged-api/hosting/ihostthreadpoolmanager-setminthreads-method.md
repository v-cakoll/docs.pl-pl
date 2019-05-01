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
ms.openlocfilehash: e290f20feacc59944bb1cafded327f4316ab88d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046218"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="4a171-102">IHostThreadPoolManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a171-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="4a171-103">Ustawia minimalna liczba bezczynnych wątków, które hosta, musisz utrzymywać w oczekiwaniu żądań.</span><span class="sxs-lookup"><span data-stu-id="4a171-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a171-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a171-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a171-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a171-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="4a171-106">[in] Nowe minimalna liczba wątków, które należy zachować hosta.</span><span class="sxs-lookup"><span data-stu-id="4a171-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a171-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4a171-107">Return Value</span></span>  
  
|<span data-ttu-id="4a171-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a171-108">HRESULT</span></span>|<span data-ttu-id="4a171-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4a171-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a171-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a171-110">S_OK</span></span>|<span data-ttu-id="4a171-111">`SetMinThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4a171-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4a171-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a171-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a171-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="4a171-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a171-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a171-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a171-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="4a171-115">The call timed out.</span></span>|  
|<span data-ttu-id="4a171-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a171-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a171-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="4a171-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a171-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a171-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a171-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="4a171-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a171-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a171-120">E_FAIL</span></span>|<span data-ttu-id="4a171-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4a171-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a171-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4a171-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a171-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a171-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a171-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4a171-124">E_NOTIMPL</span></span>|<span data-ttu-id="4a171-125">Host nie zawiera implementacji `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4a171-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a171-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a171-126">Remarks</span></span>  
 <span data-ttu-id="4a171-127">Host nie musi dostarczać implementację `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4a171-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="4a171-128">W tym przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4a171-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a171-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a171-129">Requirements</span></span>  
 <span data-ttu-id="4a171-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a171-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a171-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a171-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a171-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a171-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a171-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a171-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a171-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a171-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4a171-135">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="4a171-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="4a171-136">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="4a171-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="4a171-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a171-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
