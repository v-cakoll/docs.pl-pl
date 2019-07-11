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
ms.openlocfilehash: 8609b32ad2dea699b5b248b2b8bb3d81ec744043
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779477"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="75c8a-102">IGCThreadControl::ThreadIsBlockingForSuspension — Metoda</span><span class="sxs-lookup"><span data-stu-id="75c8a-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="75c8a-103">Powiadamia hosta, że wątek, który wykonuje wywołanie zostanie zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="75c8a-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75c8a-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="75c8a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75c8a-105">Remarks</span></span>  
 <span data-ttu-id="75c8a-106">Host może wybrać w ramach `ThreadIsBlockingForSuspension` wywołania zwrotnego czy zmienić termin egzaminu wątku.</span><span class="sxs-lookup"><span data-stu-id="75c8a-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75c8a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75c8a-107">Requirements</span></span>  
 <span data-ttu-id="75c8a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75c8a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75c8a-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75c8a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75c8a-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75c8a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75c8a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75c8a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c8a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75c8a-112">See also</span></span>

- [<span data-ttu-id="75c8a-113">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="75c8a-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
