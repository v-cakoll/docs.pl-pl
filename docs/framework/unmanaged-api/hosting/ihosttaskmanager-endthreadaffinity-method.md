---
title: IHostTaskManager::EndThreadAffinity — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb07e38542893b26595b67d6cf0fa77c522b4def
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="1b2dc-102">IHostTaskManager::EndThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b2dc-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="1b2dc-103">Powiadamia hosta, którego kod zarządzany jest zamykanie okres, w którym bieżącego zadania nie muszą zostać przeniesione do innego wątku systemu operacyjnego, po wcześniejszej wywołanie [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="1b2dc-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b2dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b2dc-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1b2dc-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1b2dc-105">Return Value</span></span>  
  
|<span data-ttu-id="1b2dc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b2dc-106">HRESULT</span></span>|<span data-ttu-id="1b2dc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1b2dc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b2dc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b2dc-108">S_OK</span></span>|<span data-ttu-id="1b2dc-109">`EndThreadAffinity` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="1b2dc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b2dc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b2dc-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b2dc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b2dc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b2dc-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-113">The call timed out.</span></span>|  
|<span data-ttu-id="1b2dc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b2dc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b2dc-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b2dc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b2dc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b2dc-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b2dc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b2dc-118">E_FAIL</span></span>|<span data-ttu-id="1b2dc-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b2dc-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b2dc-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b2dc-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="1b2dc-122">E_UNEXPECTED</span></span>|<span data-ttu-id="1b2dc-123">`EndThreadAffinity` Wywołano bez wcześniej odpowiedniego wywołania `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b2dc-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b2dc-124">Remarks</span></span>  
 <span data-ttu-id="1b2dc-125">Środowisko CLR sprawia, że do odpowiedniego wywołania `BeginThreadAffinity` na bieżące zadanie przed wywołaniem `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="1b2dc-126">W przypadku braku takiego odpowiedniego wywołania implementacja hosta [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) powinien zwrócić E_UNEXPECTED, a nie podejmuj żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="1b2dc-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b2dc-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b2dc-127">Requirements</span></span>  
 <span data-ttu-id="1b2dc-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b2dc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b2dc-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b2dc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b2dc-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b2dc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b2dc-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b2dc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b2dc-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b2dc-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="1b2dc-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b2dc-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1b2dc-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b2dc-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1b2dc-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b2dc-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1b2dc-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b2dc-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
