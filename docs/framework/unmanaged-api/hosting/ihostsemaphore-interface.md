---
title: IHostSemaphore — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: 2cf490bcd167b7a498ae21f479f616694ccb5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139478"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="9a513-102">IHostSemaphore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a513-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="9a513-103">Reprezentuje implementację semafora na hoście dla wątków.</span><span class="sxs-lookup"><span data-stu-id="9a513-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a513-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9a513-104">Methods</span></span>  
  
|<span data-ttu-id="9a513-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a513-105">Method</span></span>|<span data-ttu-id="9a513-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9a513-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a513-107">ReleaseSemaphore, metoda</span><span class="sxs-lookup"><span data-stu-id="9a513-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="9a513-108">Zwiększa liczbę wystąpień bieżącego `IHostSemaphore` o określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="9a513-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="9a513-109">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="9a513-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="9a513-110">Powoduje, że bieżące wystąpienie `IHostSemaphore` zaczeka, aż będzie własnością lub określony czas upłynął.</span><span class="sxs-lookup"><span data-stu-id="9a513-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a513-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a513-111">Requirements</span></span>  
 <span data-ttu-id="9a513-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a513-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a513-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a513-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a513-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a513-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a513-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a513-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a513-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a513-116">See also</span></span>

- [<span data-ttu-id="9a513-117">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a513-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9a513-118">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a513-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="9a513-119">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a513-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="9a513-120">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a513-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="9a513-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9a513-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
