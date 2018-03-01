---
title: "IHostGCManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7452f49df6970bf2ca49781f6a38874186bec64f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="f180d-102">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f180d-102">IHostGCManager Interface</span></span>
<span data-ttu-id="f180d-103">Udostępnia metody, które powiadamiają o hoście zdarzenia mechanizmu kolekcji garbage implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f180d-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="f180d-104">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f180d-104">Members</span></span>  
  
|<span data-ttu-id="f180d-105">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f180d-105">Member</span></span>|<span data-ttu-id="f180d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f180d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f180d-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="f180d-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="f180d-108">Powiadamia hosta, że środowisko CLR wznawia wykonywanie zadań w wątkach, które została wstrzymana na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f180d-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="f180d-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="f180d-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="f180d-110">Powiadamia hosta, że środowisko CLR wstrzymuje wykonywanie zadań do wykonania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f180d-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="f180d-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="f180d-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="f180d-112">Powiadamia hosta, który jest wątków, z którego wykonano wywołanie metody informacje mają być blokowane dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f180d-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f180d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f180d-113">Requirements</span></span>  
 <span data-ttu-id="f180d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f180d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f180d-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f180d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f180d-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f180d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f180d-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f180d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f180d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f180d-118">See Also</span></span>  
 [<span data-ttu-id="f180d-119">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f180d-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f180d-120">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f180d-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f180d-121">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f180d-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f180d-122">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f180d-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="f180d-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f180d-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
