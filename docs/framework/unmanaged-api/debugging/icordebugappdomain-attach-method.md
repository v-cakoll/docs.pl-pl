---
title: "ICorDebugAppDomain::Attach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.Attach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ba725cfe4aabab14de4b64297a038bf0b0ccec0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="035f3-102">ICorDebugAppDomain::Attach — Metoda</span><span class="sxs-lookup"><span data-stu-id="035f3-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="035f3-103">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="035f3-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="035f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="035f3-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="035f3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="035f3-105">Remarks</span></span>  
 <span data-ttu-id="035f3-106">Debuger musi być dołączony do domeny aplikacji na odbieranie zdarzeń i włączyć debugowanie stron domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="035f3-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="035f3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="035f3-107">Requirements</span></span>  
 <span data-ttu-id="035f3-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="035f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="035f3-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="035f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="035f3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="035f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="035f3-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="035f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
