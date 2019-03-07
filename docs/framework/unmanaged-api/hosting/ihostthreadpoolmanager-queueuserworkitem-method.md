---
title: IHostThreadPoolManager::QueueUserWorkItem — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03185f3f554c5454b23b0c72c42d68714488e6be
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501711"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="d0456-102">IHostThreadPoolManager::QueueUserWorkItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0456-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="d0456-103">Kolejki funkcję do wykonania i określa obiekt zawierający dane, które ma być używany przez tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="d0456-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="d0456-104">Funkcja wykonuje, gdy wątek stanie się dostępna.</span><span class="sxs-lookup"><span data-stu-id="d0456-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0456-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0456-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0456-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0456-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="d0456-107">[in] Wskaźnik funkcji, która reprezentuje funkcję do wykonania.</span><span class="sxs-lookup"><span data-stu-id="d0456-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="d0456-108">[in] Obiekt, który zawiera dane używane przez `Function`.</span><span class="sxs-lookup"><span data-stu-id="d0456-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="d0456-109">[in] Jedną z flag wartości, zgodnie z definicją dla Win32 `QueueUserWorkItem` metody, które sterują wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d0456-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0456-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0456-110">Return Value</span></span>  
  
|<span data-ttu-id="d0456-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0456-111">HRESULT</span></span>|<span data-ttu-id="d0456-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d0456-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0456-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0456-113">S_OK</span></span>|<span data-ttu-id="d0456-114">`QueueUserWorkItem` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d0456-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="d0456-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0456-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0456-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d0456-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0456-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0456-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0456-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d0456-118">The call timed out.</span></span>|  
|<span data-ttu-id="d0456-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0456-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0456-120">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d0456-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0456-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0456-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0456-122">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d0456-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0456-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0456-123">E_FAIL</span></span>|<span data-ttu-id="d0456-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d0456-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0456-125">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d0456-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0456-126">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d0456-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0456-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0456-127">Remarks</span></span>  
 <span data-ttu-id="d0456-128">`QueueUserWorkItem` umieszcza w kolejce elementu roboczego do wątku roboczego w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="d0456-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="d0456-129">Jego typy podpisu i parametru są identyczne z odpowiedniej funkcji Win32, która ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="d0456-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="d0456-130">Aby uzyskać więcej informacji zobacz dokumentację platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="d0456-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0456-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0456-131">Requirements</span></span>  
 <span data-ttu-id="d0456-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0456-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0456-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0456-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0456-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0456-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0456-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0456-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0456-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0456-136">See also</span></span>
- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="d0456-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0456-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
