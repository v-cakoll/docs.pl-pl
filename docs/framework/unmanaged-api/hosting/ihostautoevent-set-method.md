---
title: IHostAutoEvent::Set — Metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: 55fd858927743b097e5e842c0897a16d36b76733
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804989"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="a7f04-102">IHostAutoEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7f04-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="a7f04-103">Ustawia bieżące wystąpienie [IHostAutoEvent](ihostautoevent-interface.md) na sygnał.</span><span class="sxs-lookup"><span data-stu-id="a7f04-103">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f04-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7f04-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a7f04-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7f04-105">Return Value</span></span>  
  
|<span data-ttu-id="a7f04-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7f04-106">HRESULT</span></span>|<span data-ttu-id="a7f04-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a7f04-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7f04-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7f04-108">S_OK</span></span>|<span data-ttu-id="a7f04-109">`Set`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="a7f04-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="a7f04-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7f04-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7f04-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a7f04-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7f04-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7f04-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7f04-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a7f04-113">The call timed out.</span></span>|  
|<span data-ttu-id="a7f04-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7f04-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7f04-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a7f04-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7f04-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7f04-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7f04-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a7f04-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7f04-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7f04-118">E_FAIL</span></span>|<span data-ttu-id="a7f04-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a7f04-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7f04-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="a7f04-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7f04-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a7f04-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7f04-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7f04-122">Requirements</span></span>  
 <span data-ttu-id="a7f04-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f04-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f04-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7f04-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7f04-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a7f04-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7f04-126">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f04-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f04-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7f04-127">See also</span></span>

- [<span data-ttu-id="a7f04-128">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7f04-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a7f04-129">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7f04-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="a7f04-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7f04-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="a7f04-131">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7f04-131">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
