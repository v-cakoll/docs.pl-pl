---
title: IHostAutoEvent — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: a24939ac0b0808546ef3615fae4909c6c3cf8a2e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804999"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="66de1-102">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="66de1-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="66de1-103">Przedstawia reprezentację implementacji zdarzenia resetowania hosta.</span><span class="sxs-lookup"><span data-stu-id="66de1-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66de1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="66de1-104">Methods</span></span>  
  
|<span data-ttu-id="66de1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="66de1-105">Method</span></span>|<span data-ttu-id="66de1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="66de1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66de1-107">Set, metoda</span><span class="sxs-lookup"><span data-stu-id="66de1-107">Set Method</span></span>](ihostautoevent-set-method.md)|<span data-ttu-id="66de1-108">Ustawia bieżące `IHostAutoEvent` wystąpienie na sygnał.</span><span class="sxs-lookup"><span data-stu-id="66de1-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="66de1-109">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="66de1-109">Wait Method</span></span>](ihostautoevent-wait-method.md)|<span data-ttu-id="66de1-110">Powoduje, że bieżące `IHostAutoEvent` wystąpienie czeka, aż do momentu, gdy zdarzenie jest własnością lub upłynie określony czas.</span><span class="sxs-lookup"><span data-stu-id="66de1-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66de1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66de1-111">Requirements</span></span>  
 <span data-ttu-id="66de1-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66de1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66de1-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="66de1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66de1-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="66de1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66de1-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66de1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66de1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66de1-116">See also</span></span>

- [<span data-ttu-id="66de1-117">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="66de1-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="66de1-118">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="66de1-118">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="66de1-119">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="66de1-119">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="66de1-120">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="66de1-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
