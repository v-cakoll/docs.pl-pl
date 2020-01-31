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
ms.openlocfilehash: 08cf2d0bb09080296fc1fcc69b5817f4d6118765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791731"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="cecef-102">ICorDebugStepper::StepOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="cecef-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="cecef-103">Powoduje, że ICorDebugStepper to jeden krok za pomocą zawartego w nim wątku oraz do zakończenia, gdy bieżąca ramka zwraca sterowanie do ramki wywołującej.</span><span class="sxs-lookup"><span data-stu-id="cecef-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cecef-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cecef-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cecef-105">Remarks</span></span>  
 <span data-ttu-id="cecef-106">Operacja `StepOut` zostanie zakończona po powrocie z bieżącej ramki do ramki wywołującej.</span><span class="sxs-lookup"><span data-stu-id="cecef-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="cecef-107">Jeśli `StepOut` jest wywoływana w kodzie niezarządzanym, krok zakończy się, gdy bieżąca ramka powróci do zarządzanego kodu, który go wywołał.</span><span class="sxs-lookup"><span data-stu-id="cecef-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="cecef-108">W .NET Framework w wersji 2,0 nie należy używać `StepOut` z ustawioną flagą STOP_UNMANAGED, ponieważ zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cecef-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="cecef-109">(Użyj [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) , aby ustawić flagi do wykonywania krokowo). Debugery międzyoperacyjności muszą przekroczyć kod natywny.</span><span class="sxs-lookup"><span data-stu-id="cecef-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cecef-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cecef-110">Requirements</span></span>  
 <span data-ttu-id="cecef-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cecef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cecef-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cecef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cecef-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cecef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cecef-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cecef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
