---
title: "IHostIoCompletionManager::GetMaxThreads — Metoda"
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
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d02b0ba4802b72932ea6d23c66153c265a3d6498
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="549ce-102">IHostIoCompletionManager::GetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="549ce-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="549ce-103">Pobiera maksymalną liczbę wątków, które można przyznać hosta do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="549ce-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="549ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="549ce-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="549ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="549ce-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="549ce-106">[out] Wskaźnik do maksymalną liczbę wątków w puli wątków, które host może przyznać do obsługi żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="549ce-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="549ce-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="549ce-107">Return Value</span></span>  
  
|<span data-ttu-id="549ce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="549ce-108">HRESULT</span></span>|<span data-ttu-id="549ce-109">Opis</span><span class="sxs-lookup"><span data-stu-id="549ce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="549ce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="549ce-110">S_OK</span></span>|<span data-ttu-id="549ce-111">`GetMaxThreads`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="549ce-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="549ce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="549ce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="549ce-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="549ce-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="549ce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="549ce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="549ce-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="549ce-115">The call timed out.</span></span>|  
|<span data-ttu-id="549ce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="549ce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="549ce-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="549ce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="549ce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="549ce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="549ce-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="549ce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="549ce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="549ce-120">E_FAIL</span></span>|<span data-ttu-id="549ce-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="549ce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="549ce-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="549ce-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="549ce-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="549ce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="549ce-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="549ce-124">E_NOTIMPL</span></span>|<span data-ttu-id="549ce-125">Host nie zapewniać implementację elementu `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="549ce-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="549ce-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="549ce-126">Remarks</span></span>  
 <span data-ttu-id="549ce-127">Host może być wyłączną kontrolę nad to liczba wątków, które może być przydzielona do przetwarzania żądań We/Wy, powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="549ce-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="549ce-128">Z tego powodu hosta nie jest wymagane do zaimplementowania `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="549ce-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="549ce-129">W takim przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="549ce-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="549ce-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="549ce-130">Requirements</span></span>  
 <span data-ttu-id="549ce-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="549ce-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="549ce-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="549ce-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="549ce-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="549ce-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="549ce-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="549ce-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="549ce-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="549ce-135">See Also</span></span>  
 [<span data-ttu-id="549ce-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="549ce-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="549ce-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="549ce-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
