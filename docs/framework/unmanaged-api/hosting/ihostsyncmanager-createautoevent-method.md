---
title: IHostSyncManager::CreateAutoEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: ba221beaa0edce49e75f75edddaee72e1beb9747
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803500"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="da862-102">IHostSyncManager::CreateAutoEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="da862-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="da862-103">Tworzy obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="da862-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da862-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da862-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da862-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da862-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="da862-106">określoną Wskaźnik do adresu wystąpienia [IHostAutoEvent](ihostautoevent-interface.md) zaimplementowanego przez hosta lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="da862-106">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da862-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="da862-107">Return Value</span></span>  
  
|<span data-ttu-id="da862-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da862-108">HRESULT</span></span>|<span data-ttu-id="da862-109">Opis</span><span class="sxs-lookup"><span data-stu-id="da862-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da862-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="da862-110">S_OK</span></span>|<span data-ttu-id="da862-111">`CreateAutoEvent`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="da862-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="da862-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da862-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da862-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="da862-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da862-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da862-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da862-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="da862-115">The call timed out.</span></span>|  
|<span data-ttu-id="da862-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da862-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da862-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="da862-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da862-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da862-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da862-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="da862-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da862-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da862-120">E_FAIL</span></span>|<span data-ttu-id="da862-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="da862-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da862-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="da862-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da862-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="da862-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="da862-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="da862-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="da862-125">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="da862-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da862-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da862-126">Remarks</span></span>  
 <span data-ttu-id="da862-127">`CreateAutoEvent`Tworzy obiekt automatycznego zdarzenia, którego stan jest automatycznie zmieniany na niesygnalizujący po wydaniu oczekującego wątku.</span><span class="sxs-lookup"><span data-stu-id="da862-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="da862-128">Ta metoda odzwierciedla funkcję Win32 `CreateEvent` z wartością `false` określoną dla `bManualReset` parametru</span><span class="sxs-lookup"><span data-stu-id="da862-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da862-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da862-129">Requirements</span></span>  
 <span data-ttu-id="da862-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da862-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da862-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="da862-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da862-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="da862-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da862-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da862-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da862-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da862-134">See also</span></span>

- [<span data-ttu-id="da862-135">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="da862-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="da862-136">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="da862-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="da862-137">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="da862-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="da862-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="da862-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
