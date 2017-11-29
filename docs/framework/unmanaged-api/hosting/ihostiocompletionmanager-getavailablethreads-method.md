---
title: "IHostIoCompletionManager::GetAvailableThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f06e9fe0d07258fca107413d9ad328329b5456b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="468a5-102">IHostIoCompletionManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="468a5-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="468a5-103">Pobiera liczbę wątków zakończenia We/Wy, całkowita liczba wątków zarządzanych przez hosta, które nie są obecnie obsługuje żądania.</span><span class="sxs-lookup"><span data-stu-id="468a5-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="468a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="468a5-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="468a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="468a5-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="468a5-106">[out] Wskaźnik do liczby zakończenia We/Wy wątków zarządzanych przez hosta, aktualnie dostępnych do obsługi żądań.</span><span class="sxs-lookup"><span data-stu-id="468a5-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="468a5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="468a5-107">Return Value</span></span>  
  
|<span data-ttu-id="468a5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="468a5-108">HRESULT</span></span>|<span data-ttu-id="468a5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="468a5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="468a5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="468a5-110">S_OK</span></span>|<span data-ttu-id="468a5-111">`GetAvailableThreads`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="468a5-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="468a5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="468a5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="468a5-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="468a5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="468a5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="468a5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="468a5-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="468a5-115">The call timed out.</span></span>|  
|<span data-ttu-id="468a5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="468a5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="468a5-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="468a5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="468a5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="468a5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="468a5-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="468a5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="468a5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="468a5-120">E_FAIL</span></span>|<span data-ttu-id="468a5-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="468a5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="468a5-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="468a5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="468a5-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="468a5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="468a5-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="468a5-124">E_NOTIMPL</span></span>|<span data-ttu-id="468a5-125">Host nie zapewniać implementację elementu `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="468a5-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="468a5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="468a5-126">Remarks</span></span>  
 <span data-ttu-id="468a5-127">Host może być wyłączną kontrolę nad rozmiar puli wątków We/Wy wykonania powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="468a5-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="468a5-128">W związku z tym host nie jest wymagane do zaimplementowania `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="468a5-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="468a5-129">W takim przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="468a5-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="468a5-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="468a5-130">Requirements</span></span>  
 <span data-ttu-id="468a5-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="468a5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="468a5-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="468a5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="468a5-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="468a5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="468a5-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="468a5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="468a5-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="468a5-135">See Also</span></span>  
 [<span data-ttu-id="468a5-136">ICLRIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="468a5-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="468a5-137">IHostIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="468a5-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
