---
title: IHostManualEvent — Interfejs
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136783"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="9d5a0-102">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9d5a0-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="9d5a0-103">Zapewnia implementację hosta reprezentacji zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="9d5a0-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d5a0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9d5a0-104">Methods</span></span>  
  
|<span data-ttu-id="9d5a0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9d5a0-105">Method</span></span>|<span data-ttu-id="9d5a0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9d5a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d5a0-107">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="9d5a0-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="9d5a0-108">Resetuje bieżące wystąpienie `IHostManualEvent` do stanu bez sygnalizowania.</span><span class="sxs-lookup"><span data-stu-id="9d5a0-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="9d5a0-109">Set, metoda</span><span class="sxs-lookup"><span data-stu-id="9d5a0-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="9d5a0-110">Ustawia bieżące wystąpienie `IHostManualEvent` na sygnał.</span><span class="sxs-lookup"><span data-stu-id="9d5a0-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="9d5a0-111">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="9d5a0-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="9d5a0-112">Powoduje, że bieżące wystąpienie `IHostManualEvent` zaczeka, aż będzie własnością lub upłynie określony czas.</span><span class="sxs-lookup"><span data-stu-id="9d5a0-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d5a0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d5a0-113">Requirements</span></span>  
 <span data-ttu-id="9d5a0-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d5a0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d5a0-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d5a0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d5a0-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d5a0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d5a0-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d5a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5a0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d5a0-118">See also</span></span>

- [<span data-ttu-id="9d5a0-119">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d5a0-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9d5a0-120">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d5a0-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="9d5a0-121">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d5a0-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="9d5a0-122">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d5a0-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="9d5a0-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9d5a0-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
