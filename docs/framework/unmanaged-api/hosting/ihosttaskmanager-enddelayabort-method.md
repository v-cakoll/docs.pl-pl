---
title: "IHostTaskManager::EndDelayAbort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EndDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a38f024c408065ffcd0e0278b76c064ff148bc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="dadb0-102">IHostTaskManager::EndDelayAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="dadb0-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="dadb0-103">Powiadamia hosta, którego kod zarządzany jest zamykanie okres, w którym nie można przerwać bieżące zadanie, po wcześniejszej wywołanie [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="dadb0-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dadb0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dadb0-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dadb0-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dadb0-105">Return Value</span></span>  
  
|<span data-ttu-id="dadb0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dadb0-106">HRESULT</span></span>|<span data-ttu-id="dadb0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dadb0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dadb0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dadb0-108">S_OK</span></span>|<span data-ttu-id="dadb0-109">`EndDelayAbort`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dadb0-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="dadb0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dadb0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dadb0-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dadb0-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dadb0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dadb0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dadb0-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dadb0-113">The call timed out.</span></span>|  
|<span data-ttu-id="dadb0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dadb0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dadb0-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dadb0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dadb0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dadb0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dadb0-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dadb0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dadb0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dadb0-118">E_FAIL</span></span>|<span data-ttu-id="dadb0-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dadb0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dadb0-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dadb0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dadb0-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dadb0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dadb0-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="dadb0-122">E_UNEXPECTED</span></span>|<span data-ttu-id="dadb0-123">`EndDelayAbort`Wywołano bez odpowiedniego wywołania `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="dadb0-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dadb0-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dadb0-124">Remarks</span></span>  
 <span data-ttu-id="dadb0-125">Środowisko CLR sprawia, że do odpowiedniego wywołania `BeginDelayAbort` na bieżące zadanie przed wywołaniem `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="dadb0-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="dadb0-126">W przypadku braku takiego odpowiedniego wywołania implementacja hosta [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) powinien zwrócić E_UNEXPECTED z `EndDelayAbort`, a powinien Nie podejmuj żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="dadb0-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dadb0-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dadb0-127">Requirements</span></span>  
 <span data-ttu-id="dadb0-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dadb0-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dadb0-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dadb0-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dadb0-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dadb0-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dadb0-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dadb0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dadb0-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dadb0-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="dadb0-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="dadb0-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="dadb0-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dadb0-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="dadb0-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="dadb0-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="dadb0-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dadb0-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
