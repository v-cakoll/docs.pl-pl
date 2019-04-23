---
title: IHostIoCompletionManager::CloseIoCompletionPort — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32a7c8b1c1c61eddb18ade1e77af5ea973fbaadc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107565"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="03d08-102">IHostIoCompletionManager::CloseIoCompletionPort — Metoda</span><span class="sxs-lookup"><span data-stu-id="03d08-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="03d08-103">Żądania, że host Zamknij port, która została otwarta przy użyciu wcześniejszego wywołania funkcji [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="03d08-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03d08-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03d08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03d08-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="03d08-106">[in] Uchwyt portu, aby zamknąć.</span><span class="sxs-lookup"><span data-stu-id="03d08-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03d08-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03d08-107">Return Value</span></span>  
  
|<span data-ttu-id="03d08-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03d08-108">HRESULT</span></span>|<span data-ttu-id="03d08-109">Opis</span><span class="sxs-lookup"><span data-stu-id="03d08-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03d08-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="03d08-110">S_OK</span></span>|<span data-ttu-id="03d08-111">`CloseIoCompletionPort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="03d08-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="03d08-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03d08-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03d08-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="03d08-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03d08-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03d08-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03d08-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="03d08-115">The call timed out.</span></span>|  
|<span data-ttu-id="03d08-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03d08-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03d08-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="03d08-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03d08-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03d08-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03d08-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="03d08-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03d08-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03d08-120">E_FAIL</span></span>|<span data-ttu-id="03d08-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="03d08-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03d08-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="03d08-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03d08-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="03d08-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="03d08-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="03d08-124">E_INVALIDARG</span></span>|<span data-ttu-id="03d08-125">Przekazano nieprawidłowe dojście do portu.</span><span class="sxs-lookup"><span data-stu-id="03d08-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03d08-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03d08-126">Remarks</span></span>  
 <span data-ttu-id="03d08-127">`hPort` musi być dojściem do portu, który został utworzony przez wcześniejsze wywołanie `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="03d08-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03d08-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03d08-128">Requirements</span></span>  
 <span data-ttu-id="03d08-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03d08-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03d08-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03d08-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03d08-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03d08-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03d08-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03d08-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d08-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03d08-133">See also</span></span>

- [<span data-ttu-id="03d08-134">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="03d08-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="03d08-135">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="03d08-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
