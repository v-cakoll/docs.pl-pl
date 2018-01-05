---
title: "ICorDebugManagedCallback::Break — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Break
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f9d3a39859d4e44bef2622d456ae0fbac233e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="6539e-102">ICorDebugManagedCallback::Break — Metoda</span><span class="sxs-lookup"><span data-stu-id="6539e-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="6539e-103">Powiadamia debuger podczas <xref:System.Reflection.Emit.OpCodes.Break> wykonaniem instrukcji w strumieniu kodu.</span><span class="sxs-lookup"><span data-stu-id="6539e-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6539e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6539e-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6539e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6539e-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="6539e-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, która zawiera instrukcji break.</span><span class="sxs-lookup"><span data-stu-id="6539e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="6539e-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, który zawiera instrukcji break.</span><span class="sxs-lookup"><span data-stu-id="6539e-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6539e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6539e-108">Requirements</span></span>  
 <span data-ttu-id="6539e-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6539e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6539e-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6539e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6539e-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6539e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6539e-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6539e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6539e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6539e-113">See Also</span></span>  
 [<span data-ttu-id="6539e-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="6539e-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
