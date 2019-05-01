---
title: ICorDebugStepper::StepOut — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987431"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="86ba8-102">ICorDebugStepper::StepOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="86ba8-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="86ba8-103">Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku i ukończone, gdy bieżące ramce przekazuje sterowanie do wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="86ba8-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ba8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86ba8-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="86ba8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86ba8-105">Remarks</span></span>  
 <span data-ttu-id="86ba8-106">A `StepOut` operacja zakończy się po zwróceniu zwykle z bieżącej ramki do wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="86ba8-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="86ba8-107">Jeśli `StepOut` jest wywoływana, gdy w kodzie niezarządzane, ten krok zostanie ukończone, gdy bieżące ramce powraca do kodu zarządzanego, który ją wywołuje.</span><span class="sxs-lookup"><span data-stu-id="86ba8-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="86ba8-108">W programie .NET Framework 2.0, nie należy używać `StepOut` z STOP_UNMANAGED flagą zestawu, ponieważ kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="86ba8-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="86ba8-109">(Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) można ustawić flagi do przechodzenia.) Debugery międzyoperacyjny musi Wyjdź do kodu macierzystego samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="86ba8-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86ba8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86ba8-110">Requirements</span></span>  
 <span data-ttu-id="86ba8-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86ba8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86ba8-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86ba8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86ba8-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86ba8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86ba8-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86ba8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
