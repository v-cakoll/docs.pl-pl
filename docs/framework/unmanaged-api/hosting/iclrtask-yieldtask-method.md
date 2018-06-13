---
title: ICLRTask::YieldTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 821f524cc8ff7f9983f811f539e2badb2306be26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437706"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="d012b-102">ICLRTask::YieldTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="d012b-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="d012b-103">Żądania, że środowisko uruchomieniowe języka wspólnego (CLR) odłożone zadania który bieżącego [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) reprezentuje wystąpienie i być dostępne dla innych zadań czasu procesora.</span><span class="sxs-lookup"><span data-stu-id="d012b-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d012b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d012b-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d012b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d012b-105">Return Value</span></span>  
  
|<span data-ttu-id="d012b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d012b-106">HRESULT</span></span>|<span data-ttu-id="d012b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d012b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d012b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d012b-108">S_OK</span></span>|<span data-ttu-id="d012b-109">`YieldTask` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d012b-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="d012b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d012b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d012b-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d012b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d012b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d012b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d012b-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d012b-113">The call timed out.</span></span>|  
|<span data-ttu-id="d012b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d012b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d012b-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d012b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d012b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d012b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d012b-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d012b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d012b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d012b-118">E_FAIL</span></span>|<span data-ttu-id="d012b-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d012b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d012b-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d012b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d012b-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d012b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d012b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d012b-122">Remarks</span></span>  
 <span data-ttu-id="d012b-123">Wywołuje hosta `YieldTask` do żądania zasobów procesora dla innych zadań lub procesów.</span><span class="sxs-lookup"><span data-stu-id="d012b-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="d012b-124">Ta metoda jest przeznaczone głównie do kodu długotrwałe czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="d012b-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="d012b-125">Środowisko wykonawcze próbuje zawiesić zadanie który bieżącego `ICLRTask` reprezentuje wystąpienie w stanie, w których można użyć instrukcji yield czas przetwarzania ale sprawia, że żadnej gwarancji sukcesu.</span><span class="sxs-lookup"><span data-stu-id="d012b-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d012b-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d012b-126">Requirements</span></span>  
 <span data-ttu-id="d012b-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d012b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d012b-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d012b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d012b-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d012b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d012b-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d012b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d012b-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d012b-131">See Also</span></span>  
 [<span data-ttu-id="d012b-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d012b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d012b-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d012b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d012b-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d012b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d012b-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d012b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
