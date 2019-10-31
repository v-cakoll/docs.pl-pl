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
ms.openlocfilehash: 39c35884d0fb53baefafbf86391a349e141418a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141313"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="239d3-102">IHostThreadPoolManager::QueueUserWorkItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="239d3-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="239d3-103">Kolejkuje funkcję do wykonania i określa obiekt zawierający dane, które mają być używane przez tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="239d3-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="239d3-104">Funkcja jest wykonywana po udostępnieniu wątku.</span><span class="sxs-lookup"><span data-stu-id="239d3-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="239d3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="239d3-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="239d3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="239d3-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="239d3-107">podczas Wskaźnik funkcji, który reprezentuje funkcję do wykonania.</span><span class="sxs-lookup"><span data-stu-id="239d3-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="239d3-108">podczas Obiekt, który zawiera dane, które mają być używane przez `Function`.</span><span class="sxs-lookup"><span data-stu-id="239d3-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="239d3-109">podczas Jedna z wartości flag, zgodnie z definicją dla metody `QueueUserWorkItem` Win32, która kontroluje wykonanie.</span><span class="sxs-lookup"><span data-stu-id="239d3-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="239d3-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="239d3-110">Return Value</span></span>  
  
|<span data-ttu-id="239d3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="239d3-111">HRESULT</span></span>|<span data-ttu-id="239d3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="239d3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="239d3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="239d3-113">S_OK</span></span>|<span data-ttu-id="239d3-114">`QueueUserWorkItem` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="239d3-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="239d3-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="239d3-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="239d3-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="239d3-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="239d3-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="239d3-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="239d3-118">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="239d3-118">The call timed out.</span></span>|  
|<span data-ttu-id="239d3-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="239d3-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="239d3-120">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="239d3-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="239d3-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="239d3-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="239d3-122">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="239d3-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="239d3-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="239d3-123">E_FAIL</span></span>|<span data-ttu-id="239d3-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="239d3-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="239d3-125">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="239d3-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="239d3-126">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="239d3-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="239d3-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="239d3-127">Remarks</span></span>  
 <span data-ttu-id="239d3-128">`QueueUserWorkItem` kolejkuje element roboczy do wątku roboczego w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="239d3-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="239d3-129">Jego sygnatura i typy parametrów są identyczne z odpowiednimi funkcjami Win32, które mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="239d3-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="239d3-130">Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="239d3-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="239d3-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="239d3-131">Requirements</span></span>  
 <span data-ttu-id="239d3-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="239d3-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="239d3-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="239d3-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="239d3-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="239d3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="239d3-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="239d3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239d3-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="239d3-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="239d3-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="239d3-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
