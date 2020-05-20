---
title: ICLRMemoryNotificationCallback::OnMemoryNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: d88abcc523eca06c8ec50cac2d2984b26099174a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703792"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="10933-102">ICLRMemoryNotificationCallback::OnMemoryNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="10933-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="10933-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o załadowaniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="10933-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10933-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10933-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10933-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10933-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="10933-106">podczas Jedna z wartości [EMemoryAvailable —](ememoryavailable-enumeration.md) , wskazująca na to, że komputer jest aktualnie obecny.</span><span class="sxs-lookup"><span data-stu-id="10933-106">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10933-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="10933-107">Return Value</span></span>  
  
|<span data-ttu-id="10933-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10933-108">HRESULT</span></span>|<span data-ttu-id="10933-109">Opis</span><span class="sxs-lookup"><span data-stu-id="10933-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10933-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10933-110">S_OK</span></span>|<span data-ttu-id="10933-111">`OnMemoryNotification`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="10933-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="10933-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10933-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10933-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="10933-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10933-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10933-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10933-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="10933-115">The call timed out.</span></span>|  
|<span data-ttu-id="10933-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10933-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10933-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="10933-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10933-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10933-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10933-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="10933-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10933-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10933-120">E_FAIL</span></span>|<span data-ttu-id="10933-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="10933-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10933-122">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="10933-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10933-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10933-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10933-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10933-124">Remarks</span></span>  
 <span data-ttu-id="10933-125">Środowisko CLR rejestruje wywołanie zwrotne do `OnMemoryNotification` przy użyciu wywołania metody [IHostMemoryManager:: RegisterMemoryNotificationCallback —](ihostmemorymanager-registermemorynotificationcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="10933-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="10933-126">Środowisko uruchomieniowe używa informacji zwracanych w wywołaniu zwrotnym, aby zwolnić dodatkową pamięć, gdy host zgłasza, że zasoby pamięci są niskie.</span><span class="sxs-lookup"><span data-stu-id="10933-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10933-127">Wywołania `OnMemoryNotification` nigdy nie blokują.</span><span class="sxs-lookup"><span data-stu-id="10933-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="10933-128">Zawsze są zwracane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="10933-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10933-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10933-129">Requirements</span></span>  
 <span data-ttu-id="10933-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10933-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10933-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="10933-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10933-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="10933-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10933-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10933-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10933-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10933-134">See also</span></span>

- [<span data-ttu-id="10933-135">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="10933-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="10933-136">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="10933-136">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="10933-137">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="10933-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
