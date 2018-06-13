---
title: ICLRTask::SetTaskIdentifier — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a561c54f2d004d073fdfffffdb59cb2b5189e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435683"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="60afa-102">ICLRTask::SetTaskIdentifier — Metoda</span><span class="sxs-lookup"><span data-stu-id="60afa-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="60afa-103">Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR), aby skojarzyć wartość określonego identyfikatora reprezentowany przez bieżące zadanie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="60afa-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60afa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60afa-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60afa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60afa-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="60afa-106">[in] Unikatowy identyfikator dla środowiska CLR do skojarzenia z zadań reprezentowany przez bieżący `ICLRTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="60afa-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60afa-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="60afa-107">Return Value</span></span>  
  
|<span data-ttu-id="60afa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60afa-108">HRESULT</span></span>|<span data-ttu-id="60afa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="60afa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60afa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="60afa-110">S_OK</span></span>|<span data-ttu-id="60afa-111">`SetTaskIdentifier` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="60afa-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="60afa-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60afa-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60afa-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="60afa-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60afa-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60afa-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60afa-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="60afa-115">The call timed out.</span></span>|  
|<span data-ttu-id="60afa-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60afa-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60afa-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="60afa-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60afa-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60afa-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60afa-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="60afa-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60afa-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60afa-120">E_FAIL</span></span>|<span data-ttu-id="60afa-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="60afa-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60afa-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="60afa-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60afa-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="60afa-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60afa-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60afa-124">Remarks</span></span>  
 <span data-ttu-id="60afa-125">Hosta można skojarzyć identyfikatora zadania w celu integracji środowiska CLR i hosta w środowisku debugowania.</span><span class="sxs-lookup"><span data-stu-id="60afa-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="60afa-126">Identyfikator nie ma znaczenia dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="60afa-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="60afa-127">Środowisko CLR przekazuje go wzdłuż do aplikacji debugera.</span><span class="sxs-lookup"><span data-stu-id="60afa-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="60afa-128">Debuger można skojarzyć stosu wywołań CLR z stosu wywołań hosta za pomocą tego identyfikatora i Włącz informacje śledzenia odpowiednich do ujednoliconego, podczas wyświetlania w interfejsie użytkownika debugera.</span><span class="sxs-lookup"><span data-stu-id="60afa-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60afa-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60afa-129">Requirements</span></span>  
 <span data-ttu-id="60afa-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60afa-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60afa-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="60afa-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60afa-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60afa-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60afa-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60afa-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60afa-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60afa-134">See Also</span></span>  
 [<span data-ttu-id="60afa-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="60afa-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="60afa-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="60afa-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="60afa-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="60afa-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="60afa-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="60afa-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
