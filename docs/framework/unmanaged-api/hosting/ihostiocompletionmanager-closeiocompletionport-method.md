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
ms.openlocfilehash: cceced01b34f10cf38b41cfcb2a17059650f9ad9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736534"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="c6565-102">IHostIoCompletionManager::CloseIoCompletionPort — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6565-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="c6565-103">Żądania, że host Zamknij port, która została otwarta przy użyciu wcześniejszego wywołania funkcji [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="c6565-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6565-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6565-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6565-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6565-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="c6565-106">[in] Uchwyt portu, aby zamknąć.</span><span class="sxs-lookup"><span data-stu-id="c6565-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6565-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c6565-107">Return Value</span></span>  
  
|<span data-ttu-id="c6565-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6565-108">HRESULT</span></span>|<span data-ttu-id="c6565-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c6565-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6565-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6565-110">S_OK</span></span>|<span data-ttu-id="c6565-111">`CloseIoCompletionPort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="c6565-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="c6565-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6565-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6565-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c6565-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6565-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6565-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6565-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c6565-115">The call timed out.</span></span>|  
|<span data-ttu-id="c6565-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6565-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6565-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="c6565-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6565-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6565-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6565-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c6565-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6565-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6565-120">E_FAIL</span></span>|<span data-ttu-id="c6565-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c6565-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6565-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c6565-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6565-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c6565-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c6565-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c6565-124">E_INVALIDARG</span></span>|<span data-ttu-id="c6565-125">Przekazano nieprawidłowe dojście do portu.</span><span class="sxs-lookup"><span data-stu-id="c6565-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6565-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6565-126">Remarks</span></span>  
 <span data-ttu-id="c6565-127">`hPort` musi być dojściem do portu, który został utworzony przez wcześniejsze wywołanie `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="c6565-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6565-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6565-128">Requirements</span></span>  
 <span data-ttu-id="c6565-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6565-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6565-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6565-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6565-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6565-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6565-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6565-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6565-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6565-133">See also</span></span>

- [<span data-ttu-id="c6565-134">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6565-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="c6565-135">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6565-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
