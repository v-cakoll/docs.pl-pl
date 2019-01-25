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
ms.openlocfilehash: aa2872fec7765f38fba9589a6fab659e73131937
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620464"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="88cfb-102">IGCThreadControl::ThreadIsBlockingForSuspension — Metoda</span><span class="sxs-lookup"><span data-stu-id="88cfb-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="88cfb-103">Powiadamia hosta, że wątek, który wykonuje wywołanie zostanie zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="88cfb-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cfb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88cfb-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="88cfb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88cfb-105">Remarks</span></span>  
 <span data-ttu-id="88cfb-106">Host może wybrać w ramach `ThreadIsBlockingForSuspension` wywołania zwrotnego czy zmienić termin egzaminu wątku.</span><span class="sxs-lookup"><span data-stu-id="88cfb-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88cfb-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88cfb-107">Requirements</span></span>  
 <span data-ttu-id="88cfb-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88cfb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88cfb-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88cfb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88cfb-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88cfb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88cfb-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88cfb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88cfb-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88cfb-112">See also</span></span>
- [<span data-ttu-id="88cfb-113">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="88cfb-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
