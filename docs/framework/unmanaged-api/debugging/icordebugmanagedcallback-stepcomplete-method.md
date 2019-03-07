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
ms.openlocfilehash: f5b243d8c618559bd4371bf3acde1136f532f55e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476142"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="f0517-102">ICorDebugManagedCallback::StepComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0517-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="f0517-103">Powiadamia debugera, że krok została zakończona.</span><span class="sxs-lookup"><span data-stu-id="f0517-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0517-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0517-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0517-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0517-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f0517-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątku, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="f0517-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f0517-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="f0517-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="f0517-108">[in] Wskaźnik do obiektu ICorDebugStepper —, który reprezentuje krok wykonaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="f0517-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="f0517-109">[in] Wartość cordebugstepreason — wyliczenie, która wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="f0517-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0517-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0517-110">Remarks</span></span>  
 <span data-ttu-id="f0517-111">Stepper może służyć do kontynuować przechodzenie krok po kroku w razie potrzeby, chyba że debugowanie zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="f0517-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0517-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0517-112">Requirements</span></span>  
 <span data-ttu-id="f0517-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0517-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0517-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0517-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0517-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0517-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0517-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0517-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0517-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0517-117">See also</span></span>
- [<span data-ttu-id="f0517-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0517-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
