---
title: "IHostIoCompletionManager::SetMinThreads — Metoda"
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
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bd64554278fe3c684fadf95f66ce15920827908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="e83f3-102">IHostIoCompletionManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="e83f3-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="e83f3-103">Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="e83f3-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e83f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e83f3-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e83f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e83f3-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="e83f3-106">[in] Minimalna liczba wątków zakończenia We/Wy, które należy utworzyć hosta.</span><span class="sxs-lookup"><span data-stu-id="e83f3-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e83f3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e83f3-107">Return Value</span></span>  
  
|<span data-ttu-id="e83f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e83f3-108">HRESULT</span></span>|<span data-ttu-id="e83f3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e83f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e83f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e83f3-110">S_OK</span></span>|<span data-ttu-id="e83f3-111">`SetMinThreads`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e83f3-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e83f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e83f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e83f3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e83f3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e83f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e83f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e83f3-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e83f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="e83f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e83f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e83f3-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e83f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e83f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e83f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e83f3-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e83f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e83f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e83f3-120">E_FAIL</span></span>|<span data-ttu-id="e83f3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e83f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e83f3-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e83f3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e83f3-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e83f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e83f3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e83f3-124">E_NOTIMPL</span></span>|<span data-ttu-id="e83f3-125">Host nie zapewniać implementację elementu `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="e83f3-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e83f3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e83f3-126">Remarks</span></span>  
 <span data-ttu-id="e83f3-127">Host może być wyłączną kontrolę nad to liczba wątków, które może być przydzielona do przetwarzania żądań We/Wy, powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="e83f3-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e83f3-128">Z tego powodu hosta nie jest wymagane do zaimplementowania `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="e83f3-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="e83f3-129">W takim przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="e83f3-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e83f3-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e83f3-130">Requirements</span></span>  
 <span data-ttu-id="e83f3-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e83f3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e83f3-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e83f3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e83f3-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e83f3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e83f3-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e83f3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83f3-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e83f3-135">See Also</span></span>  
 [<span data-ttu-id="e83f3-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e83f3-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="e83f3-137">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="e83f3-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="e83f3-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e83f3-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
