---
title: "ICLRTask::RudeAbort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f48de1fb44d978b1d9c8960c3e44c360b0801e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="bb8c7-102">ICLRTask::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb8c7-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="bb8c7-103">Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR), aby przerwać zadanie reprezentowany przez bieżący [ICLRTask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie natychmiast i bezwarunkowo.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb8c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb8c7-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="bb8c7-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb8c7-105">Return Value</span></span>  
  
|<span data-ttu-id="bb8c7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb8c7-106">HRESULT</span></span>|<span data-ttu-id="bb8c7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bb8c7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb8c7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb8c7-108">S_OK</span></span>|<span data-ttu-id="bb8c7-109">`RudeAbort`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="bb8c7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb8c7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb8c7-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb8c7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb8c7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb8c7-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-113">The call timed out.</span></span>|  
|<span data-ttu-id="bb8c7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb8c7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb8c7-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb8c7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb8c7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb8c7-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb8c7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb8c7-118">E_FAIL</span></span>|<span data-ttu-id="bb8c7-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb8c7-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb8c7-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb8c7-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb8c7-122">Remarks</span></span>  
 <span data-ttu-id="bb8c7-123">Wywołuje hosta `RudeAbort` natychmiast przerwać zadanie.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="bb8c7-124">Finalizatory i obsługa wyjątków — procedury nie ma gwarancji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="bb8c7-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb8c7-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb8c7-125">Requirements</span></span>  
 <span data-ttu-id="bb8c7-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb8c7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb8c7-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb8c7-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb8c7-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb8c7-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb8c7-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb8c7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8c7-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb8c7-130">See Also</span></span>  
 [<span data-ttu-id="bb8c7-131">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb8c7-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="bb8c7-132">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb8c7-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="bb8c7-133">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb8c7-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="bb8c7-134">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb8c7-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
