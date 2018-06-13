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
ms.openlocfilehash: 53aaf4c23861666962e5567a6cf9eb9fffc6292f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438759"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="65c13-102">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="65c13-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="65c13-103">Udostępnia implementację hosta reprezentację zdarzeń resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="65c13-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65c13-104">Metody</span><span class="sxs-lookup"><span data-stu-id="65c13-104">Methods</span></span>  
  
|<span data-ttu-id="65c13-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="65c13-105">Method</span></span>|<span data-ttu-id="65c13-106">Opis</span><span class="sxs-lookup"><span data-stu-id="65c13-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65c13-107">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="65c13-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="65c13-108">Przywraca bieżące `IHostManualEvent` wystąpienia-sygnalizowane stan.</span><span class="sxs-lookup"><span data-stu-id="65c13-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="65c13-109">Set, metoda</span><span class="sxs-lookup"><span data-stu-id="65c13-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="65c13-110">Ustawia bieżący `IHostManualEvent` wystąpienia sygnałowego stanu.</span><span class="sxs-lookup"><span data-stu-id="65c13-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="65c13-111">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="65c13-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="65c13-112">Powoduje, że bieżący `IHostManualEvent` wystąpienia poczekać, aż należy on do lub z określoną ilością pamięci upłynie czas.</span><span class="sxs-lookup"><span data-stu-id="65c13-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65c13-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65c13-113">Requirements</span></span>  
 <span data-ttu-id="65c13-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c13-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c13-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65c13-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65c13-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65c13-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65c13-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c13-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c13-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65c13-118">See Also</span></span>  
 [<span data-ttu-id="65c13-119">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c13-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="65c13-120">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c13-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="65c13-121">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c13-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="65c13-122">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c13-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="65c13-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="65c13-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
