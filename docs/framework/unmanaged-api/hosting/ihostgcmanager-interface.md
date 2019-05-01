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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 238b054d240437df64a83a9c4daad34d4bd5d36a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992735"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="0139c-102">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0139c-102">IHostGCManager Interface</span></span>
<span data-ttu-id="0139c-103">Udostępnia metody, które powiadamiają o hoście zdarzenia w mechanizmie kolekcji wyrzucania elementów, które są implementowane przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="0139c-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="0139c-104">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0139c-104">Members</span></span>  
  
|<span data-ttu-id="0139c-105">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0139c-105">Member</span></span>|<span data-ttu-id="0139c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0139c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0139c-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="0139c-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="0139c-108">Powiadamia hosta, że środowisko CLR wznawia wykonywanie zadań w wątkach, które została wstrzymana dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0139c-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="0139c-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="0139c-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="0139c-110">Powiadamia hosta, że środowisko CLR wstrzymuje wykonywanie zadań do wykonania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0139c-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="0139c-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="0139c-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="0139c-112">Powiadamia hosta, który jest wątek, z którego wykonano wywołania metody które zamierzasz zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0139c-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0139c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0139c-113">Requirements</span></span>  
 <span data-ttu-id="0139c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0139c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0139c-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0139c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0139c-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0139c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0139c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0139c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0139c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0139c-118">See also</span></span>

- [<span data-ttu-id="0139c-119">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0139c-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0139c-120">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0139c-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0139c-121">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0139c-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0139c-122">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0139c-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="0139c-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0139c-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
