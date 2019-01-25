---
title: IHostIoCompletionManager::SetMinThreads — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a966c1827f868c51b0a4dce93e9f536e8ae0e51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659244"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="05993-102">IHostIoCompletionManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="05993-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="05993-103">Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="05993-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05993-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05993-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05993-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05993-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="05993-106">[in] Minimalna liczba wątków zakończenia operacji We/Wy, które należy utworzyć hosta.</span><span class="sxs-lookup"><span data-stu-id="05993-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05993-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="05993-107">Return Value</span></span>  
  
|<span data-ttu-id="05993-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05993-108">HRESULT</span></span>|<span data-ttu-id="05993-109">Opis</span><span class="sxs-lookup"><span data-stu-id="05993-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05993-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="05993-110">S_OK</span></span>|<span data-ttu-id="05993-111">`SetMinThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="05993-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="05993-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05993-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05993-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="05993-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05993-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05993-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05993-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="05993-115">The call timed out.</span></span>|  
|<span data-ttu-id="05993-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05993-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05993-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="05993-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05993-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05993-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05993-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="05993-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05993-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05993-120">E_FAIL</span></span>|<span data-ttu-id="05993-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="05993-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05993-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="05993-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05993-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="05993-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="05993-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="05993-124">E_NOTIMPL</span></span>|<span data-ttu-id="05993-125">Host nie zawiera implementacji `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="05993-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05993-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05993-126">Remarks</span></span>  
 <span data-ttu-id="05993-127">Host może być wyłączną kontrolę nad liczbę wątków, które może być przydzielona do przetwarzania żądań We/Wy, powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="05993-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="05993-128">Z tego powodu host nie jest wymagane do zaimplementowania `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="05993-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="05993-129">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="05993-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05993-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05993-130">Requirements</span></span>  
 <span data-ttu-id="05993-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05993-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05993-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05993-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05993-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05993-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05993-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05993-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05993-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05993-135">See also</span></span>
- [<span data-ttu-id="05993-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="05993-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="05993-137">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="05993-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="05993-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="05993-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
