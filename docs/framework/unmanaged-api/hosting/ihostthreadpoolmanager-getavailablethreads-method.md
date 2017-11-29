---
title: "IHostThreadPoolManager::GetAvailableThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11cd8de264a332cd553ad44a35355bf45039ab84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="8f982-102">IHostThreadPoolManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f982-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="8f982-103">Pobiera liczbę wątków w puli wątków, które nie są aktualnie przetwarza elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="8f982-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f982-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f982-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f982-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f982-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="8f982-106">[out] Wskaźnik do liczba wątków w puli wątków, które nie są aktualnie przetwarza elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="8f982-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f982-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8f982-107">Return Value</span></span>  
  
|<span data-ttu-id="8f982-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f982-108">HRESULT</span></span>|<span data-ttu-id="8f982-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8f982-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f982-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f982-110">S_OK</span></span>|<span data-ttu-id="8f982-111">`GetAvailableThreads`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8f982-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8f982-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f982-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f982-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8f982-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f982-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f982-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f982-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8f982-115">The call timed out.</span></span>|  
|<span data-ttu-id="8f982-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f982-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f982-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8f982-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f982-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f982-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f982-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8f982-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f982-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f982-120">E_FAIL</span></span>|<span data-ttu-id="8f982-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8f982-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f982-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8f982-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f982-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f982-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f982-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8f982-124">E_NOTIMPL</span></span>|<span data-ttu-id="8f982-125">Host nie zapewniać implementację elementu `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="8f982-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f982-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f982-126">Remarks</span></span>  
 <span data-ttu-id="8f982-127">Jeśli host nie zapewniać implementację elementu `GetAvailableThreads`, powinien on zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8f982-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f982-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f982-128">Requirements</span></span>  
 <span data-ttu-id="8f982-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f982-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f982-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f982-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f982-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f982-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f982-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f982-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f982-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f982-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="8f982-134">IHostThreadPoolManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="8f982-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
