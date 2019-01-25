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
ms.openlocfilehash: 2a053dba8f5fb8f4144968e08b6c65412f510193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727498"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="8c568-102">IGCThreadControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8c568-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="8c568-103">Udostępnia metody do uczestnictwa w planowaniu wątki, które w przeciwnym razie zostałby zablokowany dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8c568-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c568-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8c568-104">Methods</span></span>  
  
|<span data-ttu-id="8c568-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c568-105">Method</span></span>|<span data-ttu-id="8c568-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8c568-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c568-107">SuspensionEnding, metoda</span><span class="sxs-lookup"><span data-stu-id="8c568-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="8c568-108">Powiadamia hosta, czy środowisko uruchomieniowe jest wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8c568-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="8c568-109">SuspensionStarting, metoda</span><span class="sxs-lookup"><span data-stu-id="8c568-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="8c568-110">Powiadamia hosta, rozpoczyna środowiska uruchomieniowego zawieszeniu wątku wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8c568-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="8c568-111">ThreadIsBlockingForSuspension, metoda</span><span class="sxs-lookup"><span data-stu-id="8c568-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="8c568-112">Powiadamia hosta, że wątek wywołania się zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8c568-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c568-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c568-113">Requirements</span></span>  
 <span data-ttu-id="8c568-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c568-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c568-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c568-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c568-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c568-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c568-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c568-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c568-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c568-118">See also</span></span>
- [<span data-ttu-id="8c568-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8c568-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
