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
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804856"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="347e3-102">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="347e3-102">IHostGCManager Interface</span></span>
<span data-ttu-id="347e3-103">Dostarcza metody, które powiadamiają hosta zdarzeń w mechanizmie wyrzucania elementów bezużytecznych zaimplementowane przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="347e3-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="347e3-104">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="347e3-104">Members</span></span>  
  
|<span data-ttu-id="347e3-105">Członek</span><span class="sxs-lookup"><span data-stu-id="347e3-105">Member</span></span>|<span data-ttu-id="347e3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="347e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="347e3-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="347e3-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="347e3-108">Powiadamia hosta, że środowisko CLR wznawia wykonywanie zadań w wątkach, które zostały zawieszone na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="347e3-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="347e3-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="347e3-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="347e3-110">Powiadamia hosta o wstrzymaniu wykonywania zadań przez środowisko CLR w celu wykonania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="347e3-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="347e3-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="347e3-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="347e3-112">Powiadamia hosta, że wątek, z którego wykonano wywołanie metody, ma zablokować na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="347e3-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="347e3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="347e3-113">Requirements</span></span>  
 <span data-ttu-id="347e3-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="347e3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="347e3-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="347e3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="347e3-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="347e3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="347e3-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="347e3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347e3-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="347e3-118">See also</span></span>

- [<span data-ttu-id="347e3-119">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="347e3-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="347e3-120">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="347e3-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="347e3-121">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="347e3-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="347e3-122">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="347e3-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="347e3-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="347e3-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
