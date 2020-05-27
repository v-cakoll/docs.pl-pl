---
title: IHostTask::SetCLRTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: b6eac134a4ffb1813cdc6957632ce5fb9b1a5fff
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842273"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="2a269-102">IHostTask::SetCLRTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a269-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="2a269-103">Kojarzy `ICLRTask` wystąpienie z bieżącym wystąpieniem [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2a269-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a269-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a269-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a269-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a269-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="2a269-106">podczas Wskaźnik interfejsu do wystąpienia, `ICLRTask` które ma zostać skojarzone z bieżącym `IHostTask` wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="2a269-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a269-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2a269-107">Return Value</span></span>  
  
|<span data-ttu-id="2a269-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a269-108">HRESULT</span></span>|<span data-ttu-id="2a269-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2a269-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a269-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a269-110">S_OK</span></span>|<span data-ttu-id="2a269-111">`SetCLRTask`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="2a269-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="2a269-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2a269-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2a269-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2a269-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2a269-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2a269-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2a269-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2a269-115">The call timed out.</span></span>|  
|<span data-ttu-id="2a269-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a269-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2a269-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2a269-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2a269-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2a269-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2a269-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2a269-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2a269-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2a269-120">E_FAIL</span></span>|<span data-ttu-id="2a269-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2a269-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2a269-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="2a269-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2a269-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2a269-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a269-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a269-124">Remarks</span></span>  
 <span data-ttu-id="2a269-125">Środowisko CLR wywołuje `SetCLRTask` skojarzenie `ICLRTask` wystąpienia z bieżącym `IHostTask` wystąpieniem, które zostało utworzone przez wywołanie [IHostTaskManager::](ihosttaskmanager-createtask-method.md)CreateInstance.</span><span class="sxs-lookup"><span data-stu-id="2a269-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a269-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a269-126">Requirements</span></span>  
 <span data-ttu-id="2a269-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a269-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a269-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2a269-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a269-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2a269-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a269-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a269-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a269-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a269-131">See also</span></span>

- [<span data-ttu-id="2a269-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2a269-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2a269-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a269-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2a269-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a269-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2a269-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a269-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
