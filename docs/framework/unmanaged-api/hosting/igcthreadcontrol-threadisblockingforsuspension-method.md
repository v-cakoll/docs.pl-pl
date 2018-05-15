---
title: IGCThreadControl::ThreadIsBlockingForSuspension — Metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f4b767fe7134833ee2e404be30bb51bf1385ec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="4fdd8-102">IGCThreadControl::ThreadIsBlockingForSuspension — Metoda</span><span class="sxs-lookup"><span data-stu-id="4fdd8-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="4fdd8-103">Powiadamia hosta w wątku, który jest wywołania o zbliżającym się zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="4fdd8-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fdd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fdd8-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="4fdd8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fdd8-105">Remarks</span></span>  
 <span data-ttu-id="4fdd8-106">Host może wybrać w ramach `ThreadIsBlockingForSuspension` wywołania zwrotnego czy należy zaplanować wątku.</span><span class="sxs-lookup"><span data-stu-id="4fdd8-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fdd8-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4fdd8-107">Requirements</span></span>  
 <span data-ttu-id="4fdd8-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fdd8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fdd8-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4fdd8-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fdd8-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fdd8-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fdd8-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fdd8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fdd8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fdd8-112">See Also</span></span>  
 [<span data-ttu-id="4fdd8-113">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="4fdd8-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
