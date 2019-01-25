---
title: IHostTask::Alert — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b1c5132be72cfd9f70d3a81297425109f636195
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623767"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="81436-102">IHostTask::Alert — Metoda</span><span class="sxs-lookup"><span data-stu-id="81436-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="81436-103">Żądania, czy host wznawiania zadania, reprezentowane przez bieżącą [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienie, dlatego zadanie może zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="81436-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81436-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81436-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="81436-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81436-105">Return Value</span></span>  
  
|<span data-ttu-id="81436-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81436-106">HRESULT</span></span>|<span data-ttu-id="81436-107">Opis</span><span class="sxs-lookup"><span data-stu-id="81436-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81436-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="81436-108">S_OK</span></span>|<span data-ttu-id="81436-109">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="81436-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="81436-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81436-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81436-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="81436-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81436-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81436-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81436-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="81436-113">The call timed out.</span></span>|  
|<span data-ttu-id="81436-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81436-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81436-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="81436-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81436-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81436-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81436-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="81436-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81436-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81436-118">E_FAIL</span></span>|<span data-ttu-id="81436-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="81436-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81436-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="81436-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81436-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="81436-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81436-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81436-122">Remarks</span></span>  
 <span data-ttu-id="81436-123">CLR wywołuje `Alert` metody podczas <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> jest wywoływana z kodu użytkownika, lub gdy <xref:System.AppDomain> skojarzone z bieżącym <xref:System.Threading.Thread> zamyka.</span><span class="sxs-lookup"><span data-stu-id="81436-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="81436-124">Host musi zwracać natychmiast, ponieważ połączenie jest nawiązywane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="81436-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="81436-125">Jeśli host nie może od razu alert zadania, jego wznawiania przy następnym go przechodzi do stanu, w którym można otrzymywać alerty.</span><span class="sxs-lookup"><span data-stu-id="81436-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81436-126">`Alert` dotyczy tylko tych zadań, dla których minął środowiska uruchomieniowego [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartość WAIT_ALERTABLE metody takie jak [Dołącz](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="81436-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81436-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81436-127">Requirements</span></span>  
 <span data-ttu-id="81436-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81436-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81436-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81436-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81436-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81436-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81436-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81436-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81436-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81436-132">See also</span></span>
- [<span data-ttu-id="81436-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="81436-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="81436-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="81436-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="81436-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="81436-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="81436-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="81436-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
