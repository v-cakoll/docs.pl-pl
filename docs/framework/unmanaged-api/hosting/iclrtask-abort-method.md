---
title: ICLRTask::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57efd4f29ba7e28adf1af03030d7f83eb32c1c2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763675"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="0601e-102">ICLRTask::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="0601e-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="0601e-103">Żądania, że środowisko uruchomieniowe języka wspólnego (CLR) przerwać zadanie, bieżący [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="0601e-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0601e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0601e-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0601e-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0601e-105">Return Value</span></span>  
  
|<span data-ttu-id="0601e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0601e-106">HRESULT</span></span>|<span data-ttu-id="0601e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0601e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0601e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0601e-108">S_OK</span></span>|<span data-ttu-id="0601e-109">`Abort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="0601e-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="0601e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0601e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0601e-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0601e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0601e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0601e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0601e-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0601e-113">The call timed out.</span></span>|  
|<span data-ttu-id="0601e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0601e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0601e-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="0601e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0601e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0601e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0601e-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0601e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0601e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0601e-118">E_FAIL</span></span>|<span data-ttu-id="0601e-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0601e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0601e-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0601e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0601e-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0601e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0601e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0601e-122">Remarks</span></span>  
 <span data-ttu-id="0601e-123">Środowisko CLR wywołuje <xref:System.Threading.ThreadAbortException> kiedy wywołuje hosta `Abort`.</span><span class="sxs-lookup"><span data-stu-id="0601e-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="0601e-124">Zwraca natychmiast, po zainicjowaniu informacje o wyjątku, bez konieczności oczekiwania na kod użytkownika, takie jak finalizatory lub mechanizmy obsługi wyjątków, aby wykonać.</span><span class="sxs-lookup"><span data-stu-id="0601e-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="0601e-125">Wywołania `Abort` więc szybko zwracać wynik.</span><span class="sxs-lookup"><span data-stu-id="0601e-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0601e-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0601e-126">Requirements</span></span>  
 <span data-ttu-id="0601e-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0601e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0601e-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0601e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0601e-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0601e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0601e-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0601e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0601e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0601e-131">See also</span></span>

- [<span data-ttu-id="0601e-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0601e-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0601e-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0601e-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0601e-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0601e-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0601e-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0601e-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
