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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb09422872a0d9565be286c25ca1b28d1c45e08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501701"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="65f02-102">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="65f02-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="65f02-103">Udostępnia implementację hosta reprezentacji zdarzenie resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="65f02-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65f02-104">Metody</span><span class="sxs-lookup"><span data-stu-id="65f02-104">Methods</span></span>  
  
|<span data-ttu-id="65f02-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="65f02-105">Method</span></span>|<span data-ttu-id="65f02-106">Opis</span><span class="sxs-lookup"><span data-stu-id="65f02-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65f02-107">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="65f02-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="65f02-108">Przywraca bieżące `IHostManualEvent` wystąpienia do stanu zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="65f02-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="65f02-109">Set, metoda</span><span class="sxs-lookup"><span data-stu-id="65f02-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="65f02-110">Ustawia bieżący `IHostManualEvent` wystąpienie do sygnalizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="65f02-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="65f02-111">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="65f02-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="65f02-112">Powoduje, że bieżący `IHostManualEvent` wystąpienia do odczekania aż do jego właścicielem jest lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="65f02-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65f02-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65f02-113">Requirements</span></span>  
 <span data-ttu-id="65f02-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65f02-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f02-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65f02-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65f02-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65f02-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65f02-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f02-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f02-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65f02-118">See also</span></span>
- [<span data-ttu-id="65f02-119">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65f02-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="65f02-120">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="65f02-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="65f02-121">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="65f02-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="65f02-122">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65f02-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="65f02-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="65f02-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
