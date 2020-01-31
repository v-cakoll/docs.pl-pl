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
ms.openlocfilehash: e5d828b8252b47c2edddbe14713208ae8bc2d19d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777162"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="9d624-102">ICorDebugManagedCallback::StepComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d624-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="9d624-103">Powiadamia debuger o ukończeniu kroku.</span><span class="sxs-lookup"><span data-stu-id="9d624-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d624-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d624-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d624-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d624-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9d624-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą wątek, w którym krok został ukończony.</span><span class="sxs-lookup"><span data-stu-id="9d624-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9d624-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym krok został ukończony.</span><span class="sxs-lookup"><span data-stu-id="9d624-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="9d624-108">podczas Wskaźnik do obiektu ICorDebugStepper, który reprezentuje etap wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="9d624-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="9d624-109">podczas Wartość wyliczenia CorDebugStepReason —, która wskazuje wynik pojedynczego kroku.</span><span class="sxs-lookup"><span data-stu-id="9d624-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d624-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d624-110">Remarks</span></span>  
 <span data-ttu-id="9d624-111">Stepper można użyć, aby kontynuować powtarzanie w razie potrzeby, chyba że debugowanie zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="9d624-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d624-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d624-112">Requirements</span></span>  
 <span data-ttu-id="9d624-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d624-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d624-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d624-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d624-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d624-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d624-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d624-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d624-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d624-117">See also</span></span>

- [<span data-ttu-id="9d624-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d624-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
