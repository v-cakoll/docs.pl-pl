---
title: "ICLRTask::SwitchOut — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SwitchOut
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82fffd5de9735db51d9ea5f417c745736b98b53d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="97cfe-102">ICLRTask::SwitchOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="97cfe-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="97cfe-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) który zadania reprezentowany przez bieżący [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia nie jest już w stanie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="97cfe-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97cfe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97cfe-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="97cfe-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="97cfe-105">Return Value</span></span>  
  
|<span data-ttu-id="97cfe-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97cfe-106">HRESULT</span></span>|<span data-ttu-id="97cfe-107">Opis</span><span class="sxs-lookup"><span data-stu-id="97cfe-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97cfe-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="97cfe-108">S_OK</span></span>|<span data-ttu-id="97cfe-109">`SwitchOut`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="97cfe-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="97cfe-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97cfe-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97cfe-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="97cfe-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97cfe-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97cfe-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97cfe-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="97cfe-113">The call timed out.</span></span>|  
|<span data-ttu-id="97cfe-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97cfe-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97cfe-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="97cfe-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97cfe-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97cfe-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97cfe-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="97cfe-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97cfe-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97cfe-118">E_FAIL</span></span>|<span data-ttu-id="97cfe-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="97cfe-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97cfe-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="97cfe-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97cfe-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97cfe-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97cfe-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97cfe-122">Remarks</span></span>  
 <span data-ttu-id="97cfe-123">Wywołuje hosta `SwitchOut` informują CLR, że usługa została tymczasowo zatrzymana wykonywanie zadania który bieżącego `ICLRTask` reprezentuje wystąpienie i ponownie zadania.</span><span class="sxs-lookup"><span data-stu-id="97cfe-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97cfe-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97cfe-124">Requirements</span></span>  
 <span data-ttu-id="97cfe-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97cfe-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97cfe-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97cfe-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97cfe-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97cfe-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97cfe-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97cfe-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97cfe-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97cfe-129">See Also</span></span>  
 [<span data-ttu-id="97cfe-130">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="97cfe-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="97cfe-131">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="97cfe-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="97cfe-132">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="97cfe-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="97cfe-133">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="97cfe-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
