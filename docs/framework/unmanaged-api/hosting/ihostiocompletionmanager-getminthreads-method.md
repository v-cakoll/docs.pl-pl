---
title: IHostIoCompletionManager::GetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faac5adccecdd0aeecede3b4f50a4db554e3d162
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077163"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="09cc2-102">IHostIoCompletionManager::GetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="09cc2-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="09cc2-103">Pobiera minimalną liczbę wątków, udostępnianych przez hosta do przetwarzania żądań We/Wy.</span><span class="sxs-lookup"><span data-stu-id="09cc2-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09cc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09cc2-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09cc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09cc2-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="09cc2-106">[out] Wskaźnik do minimalna liczba wątków, żądań We/Wy procesu przez hosta.</span><span class="sxs-lookup"><span data-stu-id="09cc2-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09cc2-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="09cc2-107">Return Value</span></span>  
  
|<span data-ttu-id="09cc2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09cc2-108">HRESULT</span></span>|<span data-ttu-id="09cc2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="09cc2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09cc2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="09cc2-110">S_OK</span></span>|`GetMinThreads` <span data-ttu-id="09cc2-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="09cc2-111">returned successfully.</span></span>|  
|<span data-ttu-id="09cc2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09cc2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09cc2-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="09cc2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09cc2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09cc2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09cc2-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="09cc2-115">The call timed out.</span></span>|  
|<span data-ttu-id="09cc2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09cc2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09cc2-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="09cc2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09cc2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09cc2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09cc2-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="09cc2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09cc2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09cc2-120">E_FAIL</span></span>|<span data-ttu-id="09cc2-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="09cc2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09cc2-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="09cc2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09cc2-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="09cc2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="09cc2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="09cc2-124">E_NOTIMPL</span></span>|<span data-ttu-id="09cc2-125">Host nie zawiera implementacji `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="09cc2-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09cc2-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09cc2-126">Remarks</span></span>  
 <span data-ttu-id="09cc2-127">Host może być wyłączną kontrolę nad liczbę wątków przydzielony do obsługi żądań We/Wy powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="09cc2-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="09cc2-128">Z tego powodu host nie jest wymagane do zaimplementowania `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="09cc2-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="09cc2-129">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="09cc2-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09cc2-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09cc2-130">Requirements</span></span>  
 <span data-ttu-id="09cc2-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09cc2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09cc2-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09cc2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09cc2-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09cc2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="09cc2-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="09cc2-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09cc2-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09cc2-135">See also</span></span>

- [<span data-ttu-id="09cc2-136">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09cc2-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="09cc2-137">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09cc2-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
