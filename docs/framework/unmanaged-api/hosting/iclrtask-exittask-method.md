---
title: ICLRTask::ExitTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9913618f597d8e456d8db4d13883ee049c21fb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726380"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="69a6a-102">ICLRTask::ExitTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="69a6a-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="69a6a-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), zadanie jest reprezentowane przez bieżącą [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia kończy się i próbuje przeprowadzić zamknięcie zadania.</span><span class="sxs-lookup"><span data-stu-id="69a6a-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69a6a-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="69a6a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="69a6a-105">Return Value</span></span>  
  
|<span data-ttu-id="69a6a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69a6a-106">HRESULT</span></span>|<span data-ttu-id="69a6a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="69a6a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69a6a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="69a6a-108">S_OK</span></span>|<span data-ttu-id="69a6a-109">`ExitTask` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="69a6a-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="69a6a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="69a6a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="69a6a-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="69a6a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="69a6a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="69a6a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="69a6a-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="69a6a-113">The call timed out.</span></span>|  
|<span data-ttu-id="69a6a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="69a6a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="69a6a-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="69a6a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="69a6a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="69a6a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="69a6a-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="69a6a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="69a6a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="69a6a-118">E_FAIL</span></span>|<span data-ttu-id="69a6a-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="69a6a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="69a6a-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="69a6a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="69a6a-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="69a6a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69a6a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69a6a-122">Remarks</span></span>  
 <span data-ttu-id="69a6a-123">`ExitTask` próbuje czystego zamknięcia zadania, w sposób analogiczny do odłączanie wątku z biblioteki typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="69a6a-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69a6a-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69a6a-124">Requirements</span></span>  
 <span data-ttu-id="69a6a-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69a6a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69a6a-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69a6a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69a6a-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69a6a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69a6a-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69a6a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a6a-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69a6a-129">See also</span></span>
- [<span data-ttu-id="69a6a-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="69a6a-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="69a6a-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="69a6a-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="69a6a-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="69a6a-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="69a6a-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="69a6a-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
