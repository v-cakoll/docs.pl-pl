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
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805128"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="dc7dc-102">IGCThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dc7dc-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="dc7dc-103">Zapewnia metody uczestnictwa w planowaniu wątków, które w przeciwnym razie byłyby blokowane na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dc7dc-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc7dc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dc7dc-104">Methods</span></span>  
  
|<span data-ttu-id="dc7dc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dc7dc-105">Method</span></span>|<span data-ttu-id="dc7dc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dc7dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc7dc-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="dc7dc-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="dc7dc-108">Powiadamia hosta, że środowisko uruchomieniowe wznawia wątki po wyrzucaniu elementów bezużytecznych lub innym zawieszeniu.</span><span class="sxs-lookup"><span data-stu-id="dc7dc-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="dc7dc-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="dc7dc-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="dc7dc-110">Powiadamia hosta, że środowisko uruchomieniowe rozpoczyna zawieszenie wątku na wyrzucanie elementów bezużytecznych lub inne zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="dc7dc-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="dc7dc-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="dc7dc-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="dc7dc-112">Powiadamia hosta, że wątek wywołujący wywołanie ma być blokowany, prawdopodobnie na wyrzucanie elementów bezużytecznych lub innym zawieszeniu.</span><span class="sxs-lookup"><span data-stu-id="dc7dc-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc7dc-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc7dc-113">Requirements</span></span>  
 <span data-ttu-id="dc7dc-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc7dc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc7dc-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dc7dc-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc7dc-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc7dc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc7dc-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc7dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc7dc-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc7dc-118">See also</span></span>

- [<span data-ttu-id="dc7dc-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="dc7dc-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
