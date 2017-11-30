---
title: "IHostThreadPoolManager::QueueUserWorkItem — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.QueueUserWorkItem
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9948673d6988de21c83c37538fb4d7c030296e58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="487e4-102">IHostThreadPoolManager::QueueUserWorkItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="487e4-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="487e4-103">Funkcja do wykonania kolejek i określa obiekt zawierający dane, które mają być używane przez tą funkcją.</span><span class="sxs-lookup"><span data-stu-id="487e4-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="487e4-104">Funkcja jest wykonywana po udostępnieniu wątku.</span><span class="sxs-lookup"><span data-stu-id="487e4-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="487e4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="487e4-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="487e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="487e4-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="487e4-107">[in] Wskaźnik funkcji, który reprezentuje funkcja do wykonania.</span><span class="sxs-lookup"><span data-stu-id="487e4-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="487e4-108">[in] Obiekt zawierający dane, które mają być używane przez `Function`.</span><span class="sxs-lookup"><span data-stu-id="487e4-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="487e4-109">[in] Jedną z flag wartości, zgodnie z definicją Win32 `QueueUserWorkItem` metody, która kontrolować wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="487e4-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="487e4-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="487e4-110">Return Value</span></span>  
  
|<span data-ttu-id="487e4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="487e4-111">HRESULT</span></span>|<span data-ttu-id="487e4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="487e4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="487e4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="487e4-113">S_OK</span></span>|<span data-ttu-id="487e4-114">`QueueUserWorkItem`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="487e4-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="487e4-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="487e4-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="487e4-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="487e4-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="487e4-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="487e4-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="487e4-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="487e4-118">The call timed out.</span></span>|  
|<span data-ttu-id="487e4-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="487e4-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="487e4-120">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="487e4-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="487e4-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="487e4-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="487e4-122">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="487e4-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="487e4-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="487e4-123">E_FAIL</span></span>|<span data-ttu-id="487e4-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="487e4-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="487e4-125">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="487e4-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="487e4-126">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="487e4-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="487e4-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="487e4-127">Remarks</span></span>  
 <span data-ttu-id="487e4-128">`QueueUserWorkItem`umieszcza w kolejce elementu roboczego do wątku roboczego w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="487e4-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="487e4-129">Jego podpisu i parametr typy są identyczne z odpowiedniej funkcji Win32, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="487e4-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="487e4-130">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="487e4-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="487e4-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="487e4-131">Requirements</span></span>  
 <span data-ttu-id="487e4-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="487e4-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="487e4-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="487e4-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="487e4-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="487e4-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="487e4-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="487e4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="487e4-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="487e4-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="487e4-137">IHostThreadPoolManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="487e4-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
