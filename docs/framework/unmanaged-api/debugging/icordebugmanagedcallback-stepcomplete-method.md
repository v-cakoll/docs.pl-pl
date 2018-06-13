---
title: ICorDebugManagedCallback::StepComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cd6cce73a96cf522521d7cd8d0cc8024e95b93c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413260"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="b10f2-102">ICorDebugManagedCallback::StepComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="b10f2-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="b10f2-103">Powiadamia debugera, czy krok zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="b10f2-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b10f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b10f2-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b10f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b10f2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b10f2-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające wątku, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="b10f2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b10f2-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="b10f2-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="b10f2-108">[in] Wskaźnik do obiektu ICorDebugStepper —, który reprezentuje krok na wykonanie kodu.</span><span class="sxs-lookup"><span data-stu-id="b10f2-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="b10f2-109">[in] Wartość wyliczenia CorDebugStepReason wskazująca wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="b10f2-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b10f2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b10f2-110">Remarks</span></span>  
 <span data-ttu-id="b10f2-111">Stepper może służyć do kontynuować wykonywanie krok po kroku w razie potrzeby, chyba że debugowanie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="b10f2-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b10f2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b10f2-112">Requirements</span></span>  
 <span data-ttu-id="b10f2-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b10f2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b10f2-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b10f2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b10f2-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b10f2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b10f2-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b10f2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10f2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b10f2-117">See Also</span></span>  
 [<span data-ttu-id="b10f2-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b10f2-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
