---
title: "IHostTaskManager::ReverseEnterRuntime — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseEnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1c8d84cbd02527a026206d6fa172a9d3f40683fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="0b5df-102">IHostTaskManager::ReverseEnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b5df-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="0b5df-103">Powiadamia hosta, że wywołanie odbywa się na środowisko uruchomieniowe języka wspólnego (CLR) z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0b5df-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b5df-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0b5df-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0b5df-105">Return Value</span></span>  
  
|<span data-ttu-id="0b5df-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b5df-106">HRESULT</span></span>|<span data-ttu-id="0b5df-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0b5df-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b5df-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b5df-108">S_OK</span></span>|<span data-ttu-id="0b5df-109">`ReverseEnterRuntime`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0b5df-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="0b5df-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b5df-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b5df-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0b5df-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b5df-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b5df-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b5df-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0b5df-113">The call timed out.</span></span>|  
|<span data-ttu-id="0b5df-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b5df-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b5df-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0b5df-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b5df-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b5df-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b5df-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0b5df-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b5df-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b5df-118">E_FAIL</span></span>|<span data-ttu-id="0b5df-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0b5df-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b5df-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0b5df-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b5df-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b5df-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0b5df-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0b5df-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0b5df-123">Do ukończenia alokacji żądany zasób jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="0b5df-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b5df-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b5df-124">Remarks</span></span>  
 <span data-ttu-id="0b5df-125">Jeśli wywołanie do środowiska CLR z sekwencji, które powstały w kodzie zarządzanym, każdy wywołanie `ReverseEnterRuntime` odpowiada wywołaniu [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="0b5df-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b5df-126">Wywołania mogą pochodzić z kodem niezarządzanym bez zagnieżdżony.</span><span class="sxs-lookup"><span data-stu-id="0b5df-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="0b5df-127">W takim przypadku jest Brak wywołania [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), lub `ReverseLeaveRuntime`oraz liczbę wywołań `ReverseEnterRuntime` nie jest równa Liczba wywołań `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="0b5df-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5df-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b5df-128">Requirements</span></span>  
 <span data-ttu-id="0b5df-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5df-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5df-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b5df-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b5df-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b5df-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b5df-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b5df-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5df-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b5df-133">See Also</span></span>  
 [<span data-ttu-id="0b5df-134">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b5df-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0b5df-135">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b5df-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0b5df-136">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b5df-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0b5df-137">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b5df-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
