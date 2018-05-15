---
title: IGCThreadControl — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9296aedf24979624c3d7357a4d51be835716a16f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="2cd21-102">IGCThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2cd21-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="2cd21-103">Udostępnia metody do uczestnictwa w planowaniu wątków, które można zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2cd21-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cd21-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2cd21-104">Methods</span></span>  
  
|<span data-ttu-id="2cd21-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2cd21-105">Method</span></span>|<span data-ttu-id="2cd21-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2cd21-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cd21-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="2cd21-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="2cd21-108">Powiadamia host środowiska uruchomieniowego Trwa wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="2cd21-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="2cd21-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="2cd21-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="2cd21-110">Powiadamia hosta rozpoczyna środowiska uruchomieniowego zawieszeniu wątku wyrzucania elementów bezużytecznych lub innych zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="2cd21-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="2cd21-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="2cd21-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="2cd21-112">Powiadamia hosta wątku wywołania o zbliżającym się zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="2cd21-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cd21-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2cd21-113">Requirements</span></span>  
 <span data-ttu-id="2cd21-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd21-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd21-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cd21-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cd21-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cd21-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cd21-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd21-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd21-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cd21-118">See Also</span></span>  
 [<span data-ttu-id="2cd21-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2cd21-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
