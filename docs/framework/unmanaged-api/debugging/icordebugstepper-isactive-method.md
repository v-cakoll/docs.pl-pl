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
ms.openlocfilehash: dcb276e6fba6a1b46b6be630804dc6f07c211b86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420511"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="4c785-102">ICorDebugStepper::IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c785-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="4c785-103">Pobiera wartość wskazującą, czy ten ICorDebugStepper — obecnie wykonuje kroku.</span><span class="sxs-lookup"><span data-stu-id="4c785-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c785-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c785-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c785-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c785-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="4c785-106">[out] Zwraca `true` Jeśli stepper jest aktualnie wykonywany krok; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="4c785-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c785-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c785-107">Remarks</span></span>  
 <span data-ttu-id="4c785-108">Dowolną akcję kroku pozostaje aktywna do momentu otrzymania przez debuger [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) wywołania, które automatycznie dezaktywuje stepper.</span><span class="sxs-lookup"><span data-stu-id="4c785-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="4c785-109">Obiekt stepper może również zostaną wyłączone przedwcześnie wywołując [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) przed wywołania zwrotnego warunek zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="4c785-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c785-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c785-110">Requirements</span></span>  
 <span data-ttu-id="4c785-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c785-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c785-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c785-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c785-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c785-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c785-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c785-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
