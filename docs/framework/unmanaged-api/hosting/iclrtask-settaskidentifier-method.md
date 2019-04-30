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
ms.openlocfilehash: abd8848ed54b26b66090e4865f9c3a0e5c4d20db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763506"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="fa7b5-102">ICLRTask::SetTaskIdentifier — Metoda</span><span class="sxs-lookup"><span data-stu-id="fa7b5-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="fa7b5-103">Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR), aby skojarzyć wartość określonego identyfikatora z zadaniem, reprezentowane przez bieżącą [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa7b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa7b5-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa7b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa7b5-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="fa7b5-106">[in] Unikatowy identyfikator dla środowiska uruchomieniowego języka wspólnego do skojarzenia z zadaniem, reprezentowane przez bieżącą `ICLRTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa7b5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa7b5-107">Return Value</span></span>  
  
|<span data-ttu-id="fa7b5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa7b5-108">HRESULT</span></span>|<span data-ttu-id="fa7b5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fa7b5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa7b5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa7b5-110">S_OK</span></span>|<span data-ttu-id="fa7b5-111">`SetTaskIdentifier` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="fa7b5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa7b5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa7b5-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa7b5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa7b5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa7b5-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-115">The call timed out.</span></span>|  
|<span data-ttu-id="fa7b5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa7b5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa7b5-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa7b5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa7b5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa7b5-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa7b5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa7b5-120">E_FAIL</span></span>|<span data-ttu-id="fa7b5-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa7b5-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa7b5-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa7b5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa7b5-124">Remarks</span></span>  
 <span data-ttu-id="fa7b5-125">Hosta można skojarzyć identyfikatora zadania ułatwiające integrację środowiska CLR i hosta w środowisku debugowania.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="fa7b5-126">Identyfikator nie ma znaczenia dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="fa7b5-127">Środowisko CLR przekazuje on wzdłuż do aplikacji debugera.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="fa7b5-128">Debuger można skojarzyć stos wywołań CLR o stosie wywołań hosta za pomocą tego identyfikatora i włączyć informacje śledzenia odpowiednich do ujednoliconego, podczas wyświetlania w interfejsie użytkownika debugera.</span><span class="sxs-lookup"><span data-stu-id="fa7b5-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa7b5-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa7b5-129">Requirements</span></span>  
 <span data-ttu-id="fa7b5-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa7b5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa7b5-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fa7b5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa7b5-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa7b5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa7b5-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa7b5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7b5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa7b5-134">See also</span></span>

- [<span data-ttu-id="fa7b5-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b5-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fa7b5-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b5-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fa7b5-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b5-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fa7b5-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7b5-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
