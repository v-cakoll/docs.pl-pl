---
title: ICorDebugManagedCallback::EvalException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e3ab185f1ca5571656ed9b4aa4352a007da4151
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484540"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="7cef5-102">ICorDebugManagedCallback::EvalException — Metoda</span><span class="sxs-lookup"><span data-stu-id="7cef5-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="7cef5-103">Powiadamia debugera, że ocena został zakończony z powodu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7cef5-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cef5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cef5-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cef5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cef5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7cef5-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w którym przerwana oceny.</span><span class="sxs-lookup"><span data-stu-id="7cef5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7cef5-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym przerwana oceny.</span><span class="sxs-lookup"><span data-stu-id="7cef5-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="7cef5-108">[in] Wskaźnik do obiektu ICorDebugEval, który reprezentuje kod, który wykonał oceny.</span><span class="sxs-lookup"><span data-stu-id="7cef5-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cef5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cef5-109">Requirements</span></span>  
 <span data-ttu-id="7cef5-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cef5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cef5-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cef5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cef5-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cef5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cef5-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cef5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cef5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cef5-114">See also</span></span>
- [<span data-ttu-id="7cef5-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="7cef5-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
