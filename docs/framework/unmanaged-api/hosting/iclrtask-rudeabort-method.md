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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7750d50b772ff17cf9dcd05de2e2f34556714e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770477"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="b4345-102">ICLRTask::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4345-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="b4345-103">Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR), aby przerwać zadanie, reprezentowane przez bieżącą [iclrtask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia natychmiast i bezwarunkowo.</span><span class="sxs-lookup"><span data-stu-id="b4345-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4345-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4345-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="b4345-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b4345-105">Return Value</span></span>  
  
|<span data-ttu-id="b4345-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4345-106">HRESULT</span></span>|<span data-ttu-id="b4345-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4345-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4345-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4345-108">S_OK</span></span>|<span data-ttu-id="b4345-109">`RudeAbort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="b4345-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="b4345-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4345-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4345-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b4345-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b4345-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4345-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b4345-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b4345-113">The call timed out.</span></span>|  
|<span data-ttu-id="b4345-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4345-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b4345-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="b4345-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b4345-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b4345-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b4345-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b4345-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b4345-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4345-118">E_FAIL</span></span>|<span data-ttu-id="b4345-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b4345-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b4345-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b4345-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b4345-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b4345-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4345-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4345-122">Remarks</span></span>  
 <span data-ttu-id="b4345-123">Wywołuje hosta `RudeAbort` aby przerwać zadanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="b4345-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="b4345-124">Finalizatory i obsługa wyjątków — procedury nie są gwarantowane do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b4345-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4345-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4345-125">Requirements</span></span>  
 <span data-ttu-id="b4345-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4345-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4345-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4345-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4345-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4345-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4345-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4345-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4345-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4345-130">See also</span></span>

- [<span data-ttu-id="b4345-131">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4345-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b4345-132">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4345-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b4345-133">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4345-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b4345-134">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4345-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
