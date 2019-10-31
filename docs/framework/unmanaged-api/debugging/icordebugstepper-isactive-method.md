---
title: ICorDebugStepper::IsActive — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: a242764710d92e81e8089bc2919734bfac4bcdb2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137566"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="fb7b1-102">ICorDebugStepper::IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb7b1-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="fb7b1-103">Pobiera wartość wskazującą, czy ten ICorDebugStepper aktualnie wykonuje krok.</span><span class="sxs-lookup"><span data-stu-id="fb7b1-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb7b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb7b1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb7b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb7b1-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="fb7b1-106">określoną Zwraca `true`, jeśli stepper aktualnie wykonuje krok; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="fb7b1-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb7b1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb7b1-107">Remarks</span></span>  
 <span data-ttu-id="fb7b1-108">Każda akcja krok pozostaje aktywna, dopóki debuger nie otrzyma wywołania [ICorDebugManagedCallback:: StepComplete —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) , które automatycznie dezaktywuje stepper.</span><span class="sxs-lookup"><span data-stu-id="fb7b1-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="fb7b1-109">Stepper może również zostać zdezaktywowany przedwcześnie przez wywołanie [ICorDebugStepper::D eactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) przed osiągnięciem warunku wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="fb7b1-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb7b1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb7b1-110">Requirements</span></span>  
 <span data-ttu-id="fb7b1-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb7b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb7b1-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb7b1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb7b1-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fb7b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb7b1-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb7b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
