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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228888"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="75daf-102">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="75daf-102">IHostGCManager Interface</span></span>
<span data-ttu-id="75daf-103">Udostępnia metody, które powiadamiają o hoście zdarzenia w mechanizmie kolekcji wyrzucania elementów, które są implementowane przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="75daf-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="75daf-104">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="75daf-104">Members</span></span>  
  
|<span data-ttu-id="75daf-105">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="75daf-105">Member</span></span>|<span data-ttu-id="75daf-106">Opis</span><span class="sxs-lookup"><span data-stu-id="75daf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75daf-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="75daf-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="75daf-108">Powiadamia hosta, że środowisko CLR wznawia wykonywanie zadań w wątkach, które została wstrzymana dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75daf-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="75daf-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="75daf-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="75daf-110">Powiadamia hosta, że środowisko CLR wstrzymuje wykonywanie zadań do wykonania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75daf-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="75daf-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="75daf-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="75daf-112">Powiadamia hosta, który jest wątek, z którego wykonano wywołania metody które zamierzasz zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75daf-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75daf-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75daf-113">Requirements</span></span>  
 <span data-ttu-id="75daf-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75daf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75daf-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75daf-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75daf-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75daf-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75daf-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75daf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75daf-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75daf-118">See also</span></span>

- [<span data-ttu-id="75daf-119">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="75daf-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="75daf-120">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="75daf-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="75daf-121">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="75daf-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="75daf-122">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="75daf-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="75daf-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="75daf-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
