---
title: "IHostThreadPoolManager::SetMinThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab0b107c050b1c4b686f761ede75ea2349825270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="dad02-102">IHostThreadPoolManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="dad02-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="dad02-103">Ustawia minimalną liczbę bezczynności wątków, które muszą zachować hosta w oczekiwaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="dad02-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dad02-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dad02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dad02-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="dad02-106">[in] Nowe minimalna liczba wątków, które muszą zachować hosta.</span><span class="sxs-lookup"><span data-stu-id="dad02-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dad02-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dad02-107">Return Value</span></span>  
  
|<span data-ttu-id="dad02-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dad02-108">HRESULT</span></span>|<span data-ttu-id="dad02-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dad02-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dad02-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dad02-110">S_OK</span></span>|<span data-ttu-id="dad02-111">`SetMinThreads`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dad02-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="dad02-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dad02-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dad02-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dad02-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dad02-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dad02-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dad02-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dad02-115">The call timed out.</span></span>|  
|<span data-ttu-id="dad02-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dad02-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dad02-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dad02-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dad02-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dad02-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dad02-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dad02-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dad02-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dad02-120">E_FAIL</span></span>|<span data-ttu-id="dad02-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dad02-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dad02-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dad02-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dad02-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dad02-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dad02-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="dad02-124">E_NOTIMPL</span></span>|<span data-ttu-id="dad02-125">Host nie zapewniać implementację elementu `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="dad02-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dad02-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dad02-126">Remarks</span></span>  
 <span data-ttu-id="dad02-127">Host nie musi zapewniać implementację elementu `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="dad02-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="dad02-128">W takim przypadku powinien on zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="dad02-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad02-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dad02-129">Requirements</span></span>  
 <span data-ttu-id="dad02-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dad02-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dad02-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dad02-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dad02-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dad02-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dad02-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad02-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad02-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dad02-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="dad02-135">GetMinThreads — metoda</span><span class="sxs-lookup"><span data-stu-id="dad02-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="dad02-136">SetMaxThreads — metoda</span><span class="sxs-lookup"><span data-stu-id="dad02-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="dad02-137">IHostThreadPoolManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="dad02-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
