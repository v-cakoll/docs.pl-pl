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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4166b63e0bb0ae276c48abb961e381809cc9792
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471423"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="23819-102">ICorDebugStepper::IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="23819-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="23819-103">Pobiera wartość wskazującą, czy ten ICorDebugStepper — jest w trakcie wykonywania kroku.</span><span class="sxs-lookup"><span data-stu-id="23819-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23819-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23819-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23819-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23819-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="23819-106">[out] Zwraca `true` Jeśli stepper jest w trakcie wykonywania kroku; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="23819-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23819-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23819-107">Remarks</span></span>  
 <span data-ttu-id="23819-108">Akcja w kroku pozostaje aktywne, dopóki debuger nie otrzyma [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) wywołania, które automatycznie dezaktywuje stepper.</span><span class="sxs-lookup"><span data-stu-id="23819-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="23819-109">Stepper może również zostaną wyłączone przedwcześnie przez wywołanie metody [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) przed wywołania zwrotnego warunek zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="23819-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23819-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23819-110">Requirements</span></span>  
 <span data-ttu-id="23819-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23819-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23819-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23819-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23819-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23819-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23819-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23819-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
