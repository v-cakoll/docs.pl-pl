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
ms.openlocfilehash: 4316412cec26ae5698918ff65b2da65de9f36ff2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779616"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="c9bff-102">IHostIoCompletionManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9bff-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="c9bff-103">Pobiera liczbę wątków zakończenia operacji We/Wy, całkowita liczba wątków zarządzana przez hosta, które nie są obecnie obsługuje żądania.</span><span class="sxs-lookup"><span data-stu-id="c9bff-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9bff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9bff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9bff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9bff-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="c9bff-106">[out] Wskaźnik do liczby operacji We/Wy wątków uzupełniania zarządzana przez hosta, które są obecnie dostępne dla żądań obsługi.</span><span class="sxs-lookup"><span data-stu-id="c9bff-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9bff-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c9bff-107">Return Value</span></span>  
  
|<span data-ttu-id="c9bff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9bff-108">HRESULT</span></span>|<span data-ttu-id="c9bff-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c9bff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9bff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9bff-110">S_OK</span></span>|<span data-ttu-id="c9bff-111">`GetAvailableThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="c9bff-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="c9bff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9bff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9bff-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c9bff-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9bff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9bff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9bff-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c9bff-115">The call timed out.</span></span>|  
|<span data-ttu-id="c9bff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9bff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9bff-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="c9bff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9bff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9bff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9bff-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c9bff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9bff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9bff-120">E_FAIL</span></span>|<span data-ttu-id="c9bff-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c9bff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9bff-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c9bff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9bff-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9bff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c9bff-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c9bff-124">E_NOTIMPL</span></span>|<span data-ttu-id="c9bff-125">Host nie zawiera implementacji `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="c9bff-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9bff-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9bff-126">Remarks</span></span>  
 <span data-ttu-id="c9bff-127">Host może być wyłączną kontrolę nad rozmiar puli wątków zakończenia operacji We/Wy powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="c9bff-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="c9bff-128">W związku z tym, host nie jest wymagane do zaimplementowania `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="c9bff-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="c9bff-129">W tym przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="c9bff-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9bff-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9bff-130">Requirements</span></span>  
 <span data-ttu-id="c9bff-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9bff-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9bff-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9bff-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9bff-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9bff-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9bff-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9bff-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9bff-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9bff-135">See also</span></span>

- [<span data-ttu-id="c9bff-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9bff-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="c9bff-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9bff-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
