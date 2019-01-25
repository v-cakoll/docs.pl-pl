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
ms.openlocfilehash: 3e2145f321d2850468eaa73cc35a9dbd19af0480
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649491"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="65e2e-102">ICLRTask::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="65e2e-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="65e2e-103">Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR), aby przerwać zadanie, reprezentowane przez bieżącą [iclrtask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia natychmiast i bezwarunkowo.</span><span class="sxs-lookup"><span data-stu-id="65e2e-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65e2e-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="65e2e-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65e2e-105">Return Value</span></span>  
  
|<span data-ttu-id="65e2e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65e2e-106">HRESULT</span></span>|<span data-ttu-id="65e2e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="65e2e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65e2e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="65e2e-108">S_OK</span></span>|<span data-ttu-id="65e2e-109">`RudeAbort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="65e2e-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="65e2e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65e2e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65e2e-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="65e2e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65e2e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65e2e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65e2e-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="65e2e-113">The call timed out.</span></span>|  
|<span data-ttu-id="65e2e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65e2e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65e2e-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="65e2e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65e2e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65e2e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65e2e-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="65e2e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65e2e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65e2e-118">E_FAIL</span></span>|<span data-ttu-id="65e2e-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="65e2e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65e2e-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="65e2e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65e2e-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65e2e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65e2e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65e2e-122">Remarks</span></span>  
 <span data-ttu-id="65e2e-123">Wywołuje hosta `RudeAbort` aby przerwać zadanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="65e2e-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="65e2e-124">Finalizatory i obsługa wyjątków — procedury nie są gwarantowane do wykonania.</span><span class="sxs-lookup"><span data-stu-id="65e2e-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65e2e-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65e2e-125">Requirements</span></span>  
 <span data-ttu-id="65e2e-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65e2e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e2e-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65e2e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65e2e-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65e2e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65e2e-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65e2e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e2e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65e2e-130">See also</span></span>
- [<span data-ttu-id="65e2e-131">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="65e2e-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="65e2e-132">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65e2e-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="65e2e-133">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="65e2e-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="65e2e-134">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65e2e-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
