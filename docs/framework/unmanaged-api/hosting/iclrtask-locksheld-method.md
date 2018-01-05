---
title: "ICLRTask::LocksHeld — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.LocksHeld
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f985295dcc54816fc0ee31b40115360602f1afd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="a2af8-102">ICLRTask::LocksHeld — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2af8-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="a2af8-103">Pobiera liczbę blokad znajdujących się obecnie w zadania.</span><span class="sxs-lookup"><span data-stu-id="a2af8-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2af8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2af8-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2af8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2af8-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="a2af8-106">[out] Liczba blokady przechowywane w zadaniu w momencie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="a2af8-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2af8-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2af8-107">Return Value</span></span>  
  
|<span data-ttu-id="a2af8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2af8-108">HRESULT</span></span>|<span data-ttu-id="a2af8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a2af8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2af8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2af8-110">S_OK</span></span>|<span data-ttu-id="a2af8-111">`LocksHeld`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a2af8-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="a2af8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2af8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2af8-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a2af8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2af8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2af8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2af8-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a2af8-115">The call timed out.</span></span>|  
|<span data-ttu-id="a2af8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2af8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2af8-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a2af8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2af8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2af8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2af8-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a2af8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2af8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2af8-120">E_FAIL</span></span>|<span data-ttu-id="a2af8-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a2af8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2af8-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a2af8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2af8-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a2af8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2af8-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2af8-124">Requirements</span></span>  
 <span data-ttu-id="a2af8-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2af8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2af8-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2af8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2af8-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2af8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2af8-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2af8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2af8-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2af8-129">See Also</span></span>  
 [<span data-ttu-id="a2af8-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2af8-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a2af8-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2af8-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a2af8-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2af8-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a2af8-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2af8-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
