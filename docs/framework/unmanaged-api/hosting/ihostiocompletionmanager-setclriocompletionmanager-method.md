---
title: "IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetCLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2447ba9cf3ee5968bde26b0a578cc06ef5c614c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="bbf01-102">IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="bbf01-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="bbf01-103">Udostępnia wskaźnik interfejsu do hosta [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="bbf01-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbf01-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbf01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbf01-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="bbf01-106">[in] Wskaźnik interfejsu do `ICLRIoCompletionManager` wystąpienia przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="bbf01-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbf01-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bbf01-107">Return Value</span></span>  
  
|<span data-ttu-id="bbf01-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbf01-108">HRESULT</span></span>|<span data-ttu-id="bbf01-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bbf01-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbf01-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbf01-110">S_OK</span></span>|<span data-ttu-id="bbf01-111">`SetCLRIoCompletionManager`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bbf01-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="bbf01-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbf01-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbf01-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="bbf01-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbf01-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbf01-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbf01-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="bbf01-115">The call timed out.</span></span>|  
|<span data-ttu-id="bbf01-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbf01-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbf01-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="bbf01-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbf01-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbf01-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbf01-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="bbf01-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbf01-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbf01-120">E_FAIL</span></span>|<span data-ttu-id="bbf01-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bbf01-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbf01-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="bbf01-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbf01-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bbf01-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbf01-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbf01-124">Remarks</span></span>  
 <span data-ttu-id="bbf01-125">Po wywołaniu metody CLR ma `SetCLRIoCompletionManager`, hosta musi wywoływać [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) powiadomiono środowiska CLR Podczas operacji We/Wy żądanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="bbf01-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf01-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbf01-126">Requirements</span></span>  
 <span data-ttu-id="bbf01-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbf01-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbf01-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bbf01-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbf01-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bbf01-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbf01-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf01-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf01-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbf01-131">See Also</span></span>  
 [<span data-ttu-id="bbf01-132">ICLRIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="bbf01-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="bbf01-133">IHostIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="bbf01-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
