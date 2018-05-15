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
ms.openlocfilehash: bb5de5b46a46d5caa74b83f16d943edc39d08b01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="84e2d-102">IHostIoCompletionManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="84e2d-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="84e2d-103">Pobiera liczbę wątków zakończenia We/Wy, całkowita liczba wątków zarządzanych przez hosta, które nie są obecnie obsługuje żądania.</span><span class="sxs-lookup"><span data-stu-id="84e2d-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84e2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84e2d-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84e2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84e2d-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="84e2d-106">[out] Wskaźnik do liczby zakończenia We/Wy wątków zarządzanych przez hosta, aktualnie dostępnych do obsługi żądań.</span><span class="sxs-lookup"><span data-stu-id="84e2d-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84e2d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="84e2d-107">Return Value</span></span>  
  
|<span data-ttu-id="84e2d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84e2d-108">HRESULT</span></span>|<span data-ttu-id="84e2d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="84e2d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84e2d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="84e2d-110">S_OK</span></span>|<span data-ttu-id="84e2d-111">`GetAvailableThreads` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="84e2d-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="84e2d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="84e2d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="84e2d-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="84e2d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="84e2d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="84e2d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="84e2d-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="84e2d-115">The call timed out.</span></span>|  
|<span data-ttu-id="84e2d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="84e2d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="84e2d-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="84e2d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="84e2d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="84e2d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="84e2d-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="84e2d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="84e2d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="84e2d-120">E_FAIL</span></span>|<span data-ttu-id="84e2d-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="84e2d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="84e2d-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="84e2d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="84e2d-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="84e2d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="84e2d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="84e2d-124">E_NOTIMPL</span></span>|<span data-ttu-id="84e2d-125">Host nie zapewniać implementację elementu `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="84e2d-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84e2d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84e2d-126">Remarks</span></span>  
 <span data-ttu-id="84e2d-127">Host może być wyłączną kontrolę nad rozmiar puli wątków We/Wy wykonania powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="84e2d-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="84e2d-128">W związku z tym host nie jest wymagane do zaimplementowania `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="84e2d-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="84e2d-129">W takim przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="84e2d-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84e2d-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84e2d-130">Requirements</span></span>  
 <span data-ttu-id="84e2d-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84e2d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84e2d-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84e2d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84e2d-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84e2d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84e2d-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84e2d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e2d-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84e2d-135">See Also</span></span>  
 [<span data-ttu-id="84e2d-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="84e2d-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="84e2d-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="84e2d-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
