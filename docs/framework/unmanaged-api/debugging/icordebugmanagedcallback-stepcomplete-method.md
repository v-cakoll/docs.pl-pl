---
title: "ICorDebugManagedCallback::StepComplete — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.StepComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eabc9a2730a1afdf574cee97a6f1b40bae34c7ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="dba07-102">ICorDebugManagedCallback::StepComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="dba07-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="dba07-103">Powiadamia debugera, czy krok zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="dba07-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dba07-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dba07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dba07-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dba07-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające wątku, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="dba07-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="dba07-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="dba07-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="dba07-108">[in] Wskaźnik do obiektu ICorDebugStepper —, który reprezentuje krok na wykonanie kodu.</span><span class="sxs-lookup"><span data-stu-id="dba07-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="dba07-109">[in] Wartość wyliczenia CorDebugStepReason wskazująca wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="dba07-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba07-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dba07-110">Remarks</span></span>  
 <span data-ttu-id="dba07-111">Stepper może służyć do kontynuować wykonywanie krok po kroku w razie potrzeby, chyba że debugowanie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="dba07-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba07-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dba07-112">Requirements</span></span>  
 <span data-ttu-id="dba07-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba07-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba07-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dba07-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba07-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba07-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba07-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba07-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba07-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dba07-117">See Also</span></span>  
 [<span data-ttu-id="dba07-118">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="dba07-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
