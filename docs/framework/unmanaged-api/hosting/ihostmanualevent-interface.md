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
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804596"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="bca10-102">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bca10-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="bca10-103">Zapewnia implementację hosta reprezentacji zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="bca10-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bca10-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bca10-104">Methods</span></span>  
  
|<span data-ttu-id="bca10-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bca10-105">Method</span></span>|<span data-ttu-id="bca10-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bca10-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bca10-107">Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="bca10-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="bca10-108">Resetuje bieżące `IHostManualEvent` wystąpienie do stanu niesygnalizującego.</span><span class="sxs-lookup"><span data-stu-id="bca10-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="bca10-109">Set, metoda</span><span class="sxs-lookup"><span data-stu-id="bca10-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="bca10-110">Ustawia bieżące `IHostManualEvent` wystąpienie na sygnał.</span><span class="sxs-lookup"><span data-stu-id="bca10-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="bca10-111">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="bca10-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="bca10-112">Powoduje, że bieżące `IHostManualEvent` wystąpienie zaczeka, aż będzie jego właścicielem lub upłynie określony czas.</span><span class="sxs-lookup"><span data-stu-id="bca10-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bca10-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bca10-113">Requirements</span></span>  
 <span data-ttu-id="bca10-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca10-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca10-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bca10-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bca10-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bca10-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bca10-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca10-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca10-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bca10-118">See also</span></span>

- [<span data-ttu-id="bca10-119">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bca10-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="bca10-120">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bca10-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="bca10-121">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="bca10-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="bca10-122">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bca10-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="bca10-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bca10-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
