---
title: "ICorDebugManagedCallback::EvalComplete — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5715ffdf92e118b4cd16e919f10a8fdc02a06387
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="cad06-102">ICorDebugManagedCallback::EvalComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="cad06-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="cad06-103">Powiadamia debuger ocenę została ukończona.</span><span class="sxs-lookup"><span data-stu-id="cad06-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cad06-104">Syntax</span></span>  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cad06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cad06-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cad06-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, w którym została wykonana oceny.</span><span class="sxs-lookup"><span data-stu-id="cad06-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cad06-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym została wykonana oceny.</span><span class="sxs-lookup"><span data-stu-id="cad06-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="cad06-108">[in] Wskaźnik do obiektu ICorDebugEval, który reprezentuje kod, który wykonana oceny.</span><span class="sxs-lookup"><span data-stu-id="cad06-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cad06-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cad06-109">Requirements</span></span>  
 <span data-ttu-id="cad06-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cad06-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cad06-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cad06-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cad06-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cad06-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cad06-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad06-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cad06-114">See Also</span></span>  
 [<span data-ttu-id="cad06-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="cad06-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
