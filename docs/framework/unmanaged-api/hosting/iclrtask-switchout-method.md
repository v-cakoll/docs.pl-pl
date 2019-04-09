---
title: ICLRTask::SwitchOut — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a215189461bd22011462842bf02ff6c0109119fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090059"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="56f3f-102">ICLRTask::SwitchOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="56f3f-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="56f3f-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), zadanie jest reprezentowane przez bieżącą [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia nie jest już w stanie uruchamiane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="56f3f-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56f3f-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="56f3f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56f3f-105">Return Value</span></span>  
  
|<span data-ttu-id="56f3f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56f3f-106">HRESULT</span></span>|<span data-ttu-id="56f3f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="56f3f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56f3f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="56f3f-108">S_OK</span></span>|`SwitchOut` <span data-ttu-id="56f3f-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="56f3f-109">returned successfully.</span></span>|  
|<span data-ttu-id="56f3f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56f3f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56f3f-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="56f3f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56f3f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56f3f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56f3f-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="56f3f-113">The call timed out.</span></span>|  
|<span data-ttu-id="56f3f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56f3f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56f3f-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="56f3f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56f3f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56f3f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56f3f-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="56f3f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56f3f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56f3f-118">E_FAIL</span></span>|<span data-ttu-id="56f3f-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="56f3f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56f3f-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="56f3f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56f3f-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="56f3f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56f3f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56f3f-122">Remarks</span></span>  
 <span data-ttu-id="56f3f-123">Wywołuje hosta `SwitchOut` CLR poinformować, że ma tymczasowo wstrzymał wykonywanie zadania, bieżący `ICLRTask` wystąpienie reprezentuje i ponownie zadanie.</span><span class="sxs-lookup"><span data-stu-id="56f3f-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f3f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56f3f-124">Requirements</span></span>  
 <span data-ttu-id="56f3f-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f3f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f3f-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56f3f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56f3f-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56f3f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="56f3f-128">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56f3f-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56f3f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56f3f-129">See also</span></span>

- [<span data-ttu-id="56f3f-130">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56f3f-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="56f3f-131">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56f3f-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="56f3f-132">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56f3f-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="56f3f-133">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56f3f-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
