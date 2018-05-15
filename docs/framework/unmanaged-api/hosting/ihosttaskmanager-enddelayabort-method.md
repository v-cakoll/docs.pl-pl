---
title: IHostTaskManager::EndDelayAbort — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e8691461179e4f70a4617fd9487949df62f6cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="87091-102">IHostTaskManager::EndDelayAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="87091-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="87091-103">Powiadamia hosta, którego kod zarządzany jest zamykanie okres, w którym nie można przerwać bieżące zadanie, po wcześniejszej wywołanie [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="87091-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87091-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87091-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="87091-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87091-105">Return Value</span></span>  
  
|<span data-ttu-id="87091-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87091-106">HRESULT</span></span>|<span data-ttu-id="87091-107">Opis</span><span class="sxs-lookup"><span data-stu-id="87091-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87091-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="87091-108">S_OK</span></span>|<span data-ttu-id="87091-109">`EndDelayAbort` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="87091-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="87091-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87091-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87091-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="87091-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="87091-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="87091-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="87091-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="87091-113">The call timed out.</span></span>|  
|<span data-ttu-id="87091-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="87091-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="87091-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="87091-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="87091-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="87091-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="87091-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="87091-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="87091-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87091-118">E_FAIL</span></span>|<span data-ttu-id="87091-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="87091-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="87091-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="87091-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="87091-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="87091-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="87091-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="87091-122">E_UNEXPECTED</span></span>|<span data-ttu-id="87091-123">`EndDelayAbort` Wywołano bez odpowiedniego wywołania `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="87091-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87091-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87091-124">Remarks</span></span>  
 <span data-ttu-id="87091-125">Środowisko CLR sprawia, że do odpowiedniego wywołania `BeginDelayAbort` na bieżące zadanie przed wywołaniem `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="87091-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="87091-126">W przypadku braku takiego odpowiedniego wywołania implementacja hosta [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) powinien zwrócić E_UNEXPECTED z `EndDelayAbort`, a powinien Nie podejmuj żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="87091-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87091-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87091-127">Requirements</span></span>  
 <span data-ttu-id="87091-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87091-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87091-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87091-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87091-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87091-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87091-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87091-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87091-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87091-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="87091-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="87091-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="87091-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87091-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="87091-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="87091-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="87091-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87091-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
