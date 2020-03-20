---
title: ICLRTask::RudeAbort — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: aacf9de36dc39b63ed36b672e31f40704413d608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176334"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="b2952-102">ICLRTask::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2952-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="b2952-103">Nakazuje środowiska wykonawczego języka wspólnego (CLR) do przerwania zadania reprezentowane przez bieżące [wystąpienie interfejsu ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) natychmiast i bezwarunkowo.</span><span class="sxs-lookup"><span data-stu-id="b2952-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2952-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2952-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="b2952-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2952-105">Return Value</span></span>  
  
|<span data-ttu-id="b2952-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2952-106">HRESULT</span></span>|<span data-ttu-id="b2952-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b2952-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2952-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2952-108">S_OK</span></span>|<span data-ttu-id="b2952-109">`RudeAbort`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b2952-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="b2952-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2952-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2952-111">Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b2952-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2952-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2952-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2952-113">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b2952-113">The call timed out.</span></span>|  
|<span data-ttu-id="b2952-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2952-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2952-115">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b2952-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2952-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2952-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2952-117">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="b2952-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2952-118">E_fail</span><span class="sxs-lookup"><span data-stu-id="b2952-118">E_FAIL</span></span>|<span data-ttu-id="b2952-119">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="b2952-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2952-120">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b2952-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2952-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b2952-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2952-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2952-122">Remarks</span></span>  
 <span data-ttu-id="b2952-123">Host wywołuje `RudeAbort` natychmiast przerwanie zadania.</span><span class="sxs-lookup"><span data-stu-id="b2952-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="b2952-124">Finalizatory i procedury obsługi wyjątków nie są gwarantowane do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b2952-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2952-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2952-125">Requirements</span></span>  
 <span data-ttu-id="b2952-126">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2952-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2952-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2952-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2952-128">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2952-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2952-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2952-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2952-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2952-130">See also</span></span>

- [<span data-ttu-id="b2952-131">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b2952-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b2952-132">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2952-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b2952-133">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2952-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b2952-134">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2952-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
