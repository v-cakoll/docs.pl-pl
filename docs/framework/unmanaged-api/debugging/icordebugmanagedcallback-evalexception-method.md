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
ms.openlocfilehash: 20a841006d51671a491e11c4e40287baf739d191
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209828"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="7aa43-102">ICorDebugManagedCallback::EvalException — Metoda</span><span class="sxs-lookup"><span data-stu-id="7aa43-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="7aa43-103">Powiadamia debuger o przerwaniu oceny z nieobsługiwanym wyjątkem.</span><span class="sxs-lookup"><span data-stu-id="7aa43-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aa43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7aa43-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aa43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7aa43-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7aa43-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której zakończono szacowanie.</span><span class="sxs-lookup"><span data-stu-id="7aa43-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7aa43-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym zakończono szacowanie.</span><span class="sxs-lookup"><span data-stu-id="7aa43-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="7aa43-108">podczas Wskaźnik do obiektu ICorDebugEval, który reprezentuje kod, który przeprowadził ocenę.</span><span class="sxs-lookup"><span data-stu-id="7aa43-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aa43-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7aa43-109">Requirements</span></span>  
 <span data-ttu-id="7aa43-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aa43-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aa43-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7aa43-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aa43-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7aa43-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aa43-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aa43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa43-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7aa43-114">See also</span></span>

- [<span data-ttu-id="7aa43-115">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa43-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
