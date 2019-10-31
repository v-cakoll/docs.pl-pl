---
title: IHostGCManager — Interfejs
ms.date: 03/30/2017
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
ms.openlocfilehash: 6f7158bcac7ad22647104e2041da959285d2be8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130479"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="e4370-102">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e4370-102">IHostGCManager Interface</span></span>
<span data-ttu-id="e4370-103">Dostarcza metody, które powiadamiają hosta zdarzeń w mechanizmie wyrzucania elementów bezużytecznych zaimplementowane przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e4370-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="e4370-104">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e4370-104">Members</span></span>  
  
|<span data-ttu-id="e4370-105">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e4370-105">Member</span></span>|<span data-ttu-id="e4370-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e4370-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4370-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="e4370-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="e4370-108">Powiadamia hosta, że środowisko CLR wznawia wykonywanie zadań w wątkach, które zostały zawieszone na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e4370-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="e4370-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="e4370-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="e4370-110">Powiadamia hosta o wstrzymaniu wykonywania zadań przez środowisko CLR w celu wykonania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e4370-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="e4370-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="e4370-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="e4370-112">Powiadamia hosta, że wątek, z którego wykonano wywołanie metody, ma zablokować na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e4370-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4370-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4370-113">Requirements</span></span>  
 <span data-ttu-id="e4370-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4370-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4370-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4370-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4370-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4370-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4370-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4370-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4370-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4370-118">See also</span></span>

- [<span data-ttu-id="e4370-119">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4370-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e4370-120">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4370-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e4370-121">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4370-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e4370-122">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4370-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="e4370-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e4370-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
