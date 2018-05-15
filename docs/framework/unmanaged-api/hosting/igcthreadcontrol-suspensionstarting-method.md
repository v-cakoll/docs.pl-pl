---
title: IGCThreadControl::SuspensionStarting — Metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95cbda3729c02b95557f9f700f1ea7c68aa450a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="84f46-102">IGCThreadControl::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="84f46-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="84f46-103">Powiadamia hosta rozpoczyna środowiska uruchomieniowego zawieszeniu wątku wyrzucania elementów bezużytecznych lub innych zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="84f46-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84f46-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="84f46-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84f46-105">Remarks</span></span>  
 <span data-ttu-id="84f46-106">Nie zaplanować jakieś wątki podczas `SuspensionStarting` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="84f46-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84f46-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84f46-107">Requirements</span></span>  
 <span data-ttu-id="84f46-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84f46-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84f46-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84f46-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84f46-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84f46-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84f46-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84f46-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f46-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84f46-112">See Also</span></span>  
 [<span data-ttu-id="84f46-113">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="84f46-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
