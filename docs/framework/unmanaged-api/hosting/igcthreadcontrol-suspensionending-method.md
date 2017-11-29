---
title: "IGCThreadControl::SuspensionEnding — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4460d2b0eaf10d20ddd0c3641279a8ffc05c245
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="d66f0-102">IGCThreadControl::SuspensionEnding — Metoda</span><span class="sxs-lookup"><span data-stu-id="d66f0-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="d66f0-103">Powiadamia host środowiska uruchomieniowego Trwa wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="d66f0-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d66f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d66f0-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d66f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d66f0-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="d66f0-106">[in] Generowanie, na którym ma zostać wykonane wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d66f0-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d66f0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d66f0-107">Remarks</span></span>  
 <span data-ttu-id="d66f0-108">Nie zaplanować jakieś wątki podczas `SuspensionEnding` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d66f0-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d66f0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d66f0-109">Requirements</span></span>  
 <span data-ttu-id="d66f0-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d66f0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d66f0-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d66f0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d66f0-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d66f0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d66f0-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d66f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66f0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d66f0-114">See Also</span></span>  
 [<span data-ttu-id="d66f0-115">IGCThreadControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="d66f0-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
