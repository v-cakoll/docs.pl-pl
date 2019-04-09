---
title: IHostIoCompletionManager::GetAvailableThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e96a12bbf9c4fdc8a0bc79661070eb7fec1a593
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123981"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="f51c0-102">IHostIoCompletionManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="f51c0-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="f51c0-103">Pobiera liczbę wątków zakończenia operacji We/Wy, całkowita liczba wątków zarządzana przez hosta, które nie są obecnie obsługuje żądania.</span><span class="sxs-lookup"><span data-stu-id="f51c0-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f51c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f51c0-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f51c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f51c0-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="f51c0-106">[out] Wskaźnik do liczby operacji We/Wy wątków uzupełniania zarządzana przez hosta, które są obecnie dostępne dla żądań obsługi.</span><span class="sxs-lookup"><span data-stu-id="f51c0-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f51c0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f51c0-107">Return Value</span></span>  
  
|<span data-ttu-id="f51c0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f51c0-108">HRESULT</span></span>|<span data-ttu-id="f51c0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f51c0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f51c0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f51c0-110">S_OK</span></span>|`GetAvailableThreads` <span data-ttu-id="f51c0-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="f51c0-111">returned successfully.</span></span>|  
|<span data-ttu-id="f51c0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f51c0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f51c0-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f51c0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f51c0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f51c0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f51c0-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f51c0-115">The call timed out.</span></span>|  
|<span data-ttu-id="f51c0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f51c0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f51c0-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="f51c0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f51c0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f51c0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f51c0-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f51c0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f51c0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f51c0-120">E_FAIL</span></span>|<span data-ttu-id="f51c0-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f51c0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f51c0-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f51c0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f51c0-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f51c0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f51c0-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f51c0-124">E_NOTIMPL</span></span>|<span data-ttu-id="f51c0-125">Host nie zawiera implementacji `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="f51c0-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f51c0-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f51c0-126">Remarks</span></span>  
 <span data-ttu-id="f51c0-127">Host może być wyłączną kontrolę nad rozmiar puli wątków zakończenia operacji We/Wy powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="f51c0-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="f51c0-128">W związku z tym, host nie jest wymagane do zaimplementowania `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="f51c0-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="f51c0-129">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="f51c0-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f51c0-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f51c0-130">Requirements</span></span>  
 <span data-ttu-id="f51c0-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f51c0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f51c0-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f51c0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f51c0-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f51c0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f51c0-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f51c0-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f51c0-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f51c0-135">See also</span></span>

- [<span data-ttu-id="f51c0-136">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f51c0-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f51c0-137">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f51c0-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
