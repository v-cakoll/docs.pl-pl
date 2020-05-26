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
ms.openlocfilehash: 8345d85502087568cb05dd262cccf181e3ca07ac
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803695"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="e7d20-102">IHostSemaphore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e7d20-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="e7d20-103">Reprezentuje implementację semafora na hoście dla wątków.</span><span class="sxs-lookup"><span data-stu-id="e7d20-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7d20-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e7d20-104">Methods</span></span>  
  
|<span data-ttu-id="e7d20-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e7d20-105">Method</span></span>|<span data-ttu-id="e7d20-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e7d20-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7d20-107">ReleaseSemaphore, metoda</span><span class="sxs-lookup"><span data-stu-id="e7d20-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="e7d20-108">Zwiększa liczbę `IHostSemaphore` wystąpień bieżącego wystąpienia o określoną liczbę.</span><span class="sxs-lookup"><span data-stu-id="e7d20-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="e7d20-109">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="e7d20-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="e7d20-110">Powoduje, że bieżące `IHostSemaphore` wystąpienie zaczeka, aż będzie własnością lub określony czas upłynął.</span><span class="sxs-lookup"><span data-stu-id="e7d20-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7d20-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7d20-111">Requirements</span></span>  
 <span data-ttu-id="e7d20-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d20-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d20-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e7d20-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7d20-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e7d20-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7d20-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d20-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d20-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7d20-116">See also</span></span>

- [<span data-ttu-id="e7d20-117">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e7d20-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e7d20-118">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e7d20-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="e7d20-119">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7d20-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="e7d20-120">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7d20-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="e7d20-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e7d20-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
