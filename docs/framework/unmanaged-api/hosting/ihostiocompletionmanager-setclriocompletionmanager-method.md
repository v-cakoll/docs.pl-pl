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
ms.workload: dotnet
ms.openlocfilehash: 4fde1045fd0f15e7255a163c1f1b041800e85921
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="24e07-102">IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="24e07-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="24e07-103">Udostępnia wskaźnik interfejsu do hosta [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="24e07-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24e07-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24e07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24e07-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="24e07-106">[in] Wskaźnik interfejsu do `ICLRIoCompletionManager` wystąpienia przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="24e07-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24e07-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24e07-107">Return Value</span></span>  
  
|<span data-ttu-id="24e07-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24e07-108">HRESULT</span></span>|<span data-ttu-id="24e07-109">Opis</span><span class="sxs-lookup"><span data-stu-id="24e07-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24e07-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="24e07-110">S_OK</span></span>|<span data-ttu-id="24e07-111">`SetCLRIoCompletionManager`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="24e07-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="24e07-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24e07-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24e07-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="24e07-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="24e07-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="24e07-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="24e07-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="24e07-115">The call timed out.</span></span>|  
|<span data-ttu-id="24e07-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="24e07-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="24e07-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="24e07-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="24e07-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="24e07-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="24e07-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="24e07-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="24e07-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24e07-120">E_FAIL</span></span>|<span data-ttu-id="24e07-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="24e07-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="24e07-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="24e07-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="24e07-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="24e07-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24e07-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24e07-124">Remarks</span></span>  
 <span data-ttu-id="24e07-125">Po wywołaniu metody CLR ma `SetCLRIoCompletionManager`, hosta musi wywoływać [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) powiadomiono środowiska CLR Podczas operacji We/Wy żądanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="24e07-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e07-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24e07-126">Requirements</span></span>  
 <span data-ttu-id="24e07-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24e07-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24e07-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24e07-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24e07-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24e07-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24e07-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24e07-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e07-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24e07-131">See Also</span></span>  
 [<span data-ttu-id="24e07-132">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="24e07-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="24e07-133">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="24e07-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
