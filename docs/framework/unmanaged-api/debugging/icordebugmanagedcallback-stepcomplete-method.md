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
ms.openlocfilehash: fd784cb3322423e9309e8a5632822831b4e44cdf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184798"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="15640-102">ICorDebugManagedCallback::StepComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="15640-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="15640-103">Powiadamia debugera, że krok została zakończona.</span><span class="sxs-lookup"><span data-stu-id="15640-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15640-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15640-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15640-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15640-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="15640-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątku, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="15640-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="15640-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym kroku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="15640-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="15640-108">[in] Wskaźnik do obiektu ICorDebugStepper —, który reprezentuje krok wykonaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="15640-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="15640-109">[in] Wartość cordebugstepreason — wyliczenie, która wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="15640-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15640-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15640-110">Remarks</span></span>  
 <span data-ttu-id="15640-111">Stepper może służyć do kontynuować przechodzenie krok po kroku w razie potrzeby, chyba że debugowanie zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="15640-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15640-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15640-112">Requirements</span></span>  
 <span data-ttu-id="15640-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15640-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15640-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15640-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15640-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15640-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15640-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15640-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15640-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15640-117">See also</span></span>

- [<span data-ttu-id="15640-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="15640-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
