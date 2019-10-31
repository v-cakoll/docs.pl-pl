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
ms.openlocfilehash: 3aba31f60af25144b9f01aa9ca8cc633d4c1a438
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134801"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="77be7-102">IGCThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="77be7-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="77be7-103">Zapewnia metody uczestnictwa w planowaniu wątków, które w przeciwnym razie byłyby blokowane na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="77be7-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77be7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="77be7-104">Methods</span></span>  
  
|<span data-ttu-id="77be7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="77be7-105">Method</span></span>|<span data-ttu-id="77be7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="77be7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77be7-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="77be7-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="77be7-108">Powiadamia hosta, że środowisko uruchomieniowe wznawia wątki po wyrzucaniu elementów bezużytecznych lub innym zawieszeniu.</span><span class="sxs-lookup"><span data-stu-id="77be7-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="77be7-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="77be7-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="77be7-110">Powiadamia hosta, że środowisko uruchomieniowe rozpoczyna zawieszenie wątku na wyrzucanie elementów bezużytecznych lub inne zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="77be7-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="77be7-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="77be7-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="77be7-112">Powiadamia hosta, że wątek wywołujący wywołanie ma być blokowany, prawdopodobnie na wyrzucanie elementów bezużytecznych lub innym zawieszeniu.</span><span class="sxs-lookup"><span data-stu-id="77be7-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77be7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77be7-113">Requirements</span></span>  
 <span data-ttu-id="77be7-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77be7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77be7-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="77be7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77be7-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="77be7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77be7-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77be7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77be7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77be7-118">See also</span></span>

- [<span data-ttu-id="77be7-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="77be7-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
