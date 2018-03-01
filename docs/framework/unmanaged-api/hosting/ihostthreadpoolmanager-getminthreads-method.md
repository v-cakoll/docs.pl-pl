---
title: "IHostThreadPoolManager::GetMinThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 393400c7a5d9d4d99431cbea4a3c3c82064218f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="538cf-102">IHostThreadPoolManager::GetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="538cf-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="538cf-103">Pobiera minimalna liczba wątków bezczynności, która jest obsługiwana przez hosta w puli wątków w oczekiwaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="538cf-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="538cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="538cf-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="538cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="538cf-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="538cf-106">[out] Wskaźnik do minimalna liczba wątków roboczych bezczynności, która jest aktualnie obsługiwana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="538cf-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="538cf-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="538cf-107">Return Value</span></span>  
  
|<span data-ttu-id="538cf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="538cf-108">HRESULT</span></span>|<span data-ttu-id="538cf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="538cf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="538cf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="538cf-110">S_OK</span></span>|<span data-ttu-id="538cf-111">`GetMinThreads`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="538cf-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="538cf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="538cf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="538cf-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="538cf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="538cf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="538cf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="538cf-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="538cf-115">The call timed out.</span></span>|  
|<span data-ttu-id="538cf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="538cf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="538cf-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="538cf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="538cf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="538cf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="538cf-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="538cf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="538cf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="538cf-120">E_FAIL</span></span>|<span data-ttu-id="538cf-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="538cf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="538cf-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="538cf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="538cf-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="538cf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="538cf-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="538cf-124">E_NOTIMPL</span></span>|<span data-ttu-id="538cf-125">Host nie zapewniać implementację elementu `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="538cf-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="538cf-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="538cf-126">Remarks</span></span>  
 <span data-ttu-id="538cf-127">Host nie musi zapewniać implementację elementu `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="538cf-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="538cf-128">W takim przypadku powinien on zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="538cf-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="538cf-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="538cf-129">Requirements</span></span>  
 <span data-ttu-id="538cf-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="538cf-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="538cf-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="538cf-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="538cf-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="538cf-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="538cf-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="538cf-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="538cf-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="538cf-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="538cf-135">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="538cf-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="538cf-136">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="538cf-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="538cf-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="538cf-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
