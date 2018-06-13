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
ms.openlocfilehash: 8f9852034f6d8208bdaa9b424f689adc374bae2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443683"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="43ef7-102">IHostThreadPoolManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="43ef7-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="43ef7-103">Ustawia minimalną liczbę bezczynności wątków, które muszą zachować hosta w oczekiwaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="43ef7-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ef7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43ef7-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43ef7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43ef7-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="43ef7-106">[in] Nowe minimalna liczba wątków, które muszą zachować hosta.</span><span class="sxs-lookup"><span data-stu-id="43ef7-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43ef7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="43ef7-107">Return Value</span></span>  
  
|<span data-ttu-id="43ef7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43ef7-108">HRESULT</span></span>|<span data-ttu-id="43ef7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="43ef7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43ef7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="43ef7-110">S_OK</span></span>|<span data-ttu-id="43ef7-111">`SetMinThreads` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="43ef7-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="43ef7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43ef7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43ef7-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="43ef7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43ef7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43ef7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43ef7-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="43ef7-115">The call timed out.</span></span>|  
|<span data-ttu-id="43ef7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43ef7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43ef7-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="43ef7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43ef7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43ef7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43ef7-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="43ef7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43ef7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43ef7-120">E_FAIL</span></span>|<span data-ttu-id="43ef7-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="43ef7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43ef7-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="43ef7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43ef7-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="43ef7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="43ef7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="43ef7-124">E_NOTIMPL</span></span>|<span data-ttu-id="43ef7-125">Host nie zapewniać implementację elementu `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="43ef7-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ef7-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43ef7-126">Remarks</span></span>  
 <span data-ttu-id="43ef7-127">Host nie musi zapewniać implementację elementu `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="43ef7-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="43ef7-128">W takim przypadku powinien on zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="43ef7-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ef7-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43ef7-129">Requirements</span></span>  
 <span data-ttu-id="43ef7-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ef7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ef7-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43ef7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43ef7-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43ef7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43ef7-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ef7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ef7-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43ef7-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="43ef7-135">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="43ef7-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="43ef7-136">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="43ef7-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="43ef7-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="43ef7-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
