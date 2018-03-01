---
title: "IGCThreadControl — Interfejs"
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
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: def6ae3c8bf8eea9cb135529e2b6e672b180e68c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="68f6a-102">IGCThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="68f6a-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="68f6a-103">Udostępnia metody do uczestnictwa w planowaniu wątków, które można zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="68f6a-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68f6a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="68f6a-104">Methods</span></span>  
  
|<span data-ttu-id="68f6a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="68f6a-105">Method</span></span>|<span data-ttu-id="68f6a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="68f6a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68f6a-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="68f6a-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="68f6a-108">Powiadamia host środowiska uruchomieniowego Trwa wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="68f6a-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="68f6a-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="68f6a-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="68f6a-110">Powiadamia hosta rozpoczyna środowiska uruchomieniowego zawieszeniu wątku wyrzucania elementów bezużytecznych lub innych zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="68f6a-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="68f6a-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="68f6a-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="68f6a-112">Powiadamia hosta wątku wywołania o zbliżającym się zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="68f6a-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68f6a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68f6a-113">Requirements</span></span>  
 <span data-ttu-id="68f6a-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f6a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f6a-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="68f6a-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68f6a-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68f6a-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68f6a-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f6a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f6a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68f6a-118">See Also</span></span>  
 [<span data-ttu-id="68f6a-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="68f6a-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
