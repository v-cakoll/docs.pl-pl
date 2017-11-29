---
title: "ICorDebugManagedCallback::EvalException — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EvalException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed64c7b28d60e966e836ac75e6dd7c0848304a38
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="99aa3-102">ICorDebugManagedCallback::EvalException — Metoda</span><span class="sxs-lookup"><span data-stu-id="99aa3-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="99aa3-103">Powiadamia debugera, że ocenę został zakończony z powodu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="99aa3-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99aa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99aa3-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99aa3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99aa3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="99aa3-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, w którym zakończone oceny.</span><span class="sxs-lookup"><span data-stu-id="99aa3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="99aa3-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym zakończone oceny.</span><span class="sxs-lookup"><span data-stu-id="99aa3-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="99aa3-108">[in] Wskaźnik do obiektu ICorDebugEval, który reprezentuje kod, który wykonana oceny.</span><span class="sxs-lookup"><span data-stu-id="99aa3-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99aa3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99aa3-109">Requirements</span></span>  
 <span data-ttu-id="99aa3-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99aa3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99aa3-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99aa3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99aa3-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99aa3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99aa3-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99aa3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99aa3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99aa3-114">See Also</span></span>  
 [<span data-ttu-id="99aa3-115">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="99aa3-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
