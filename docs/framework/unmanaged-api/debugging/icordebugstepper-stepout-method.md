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
ms.openlocfilehash: 9f6962f987079da1ccb04ea368307d7c119910a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379504"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="b5166-102">ICorDebugStepper::StepOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5166-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="b5166-103">Powoduje, że ICorDebugStepper to jeden krok za pomocą zawartego w nim wątku oraz do zakończenia, gdy bieżąca ramka zwraca sterowanie do ramki wywołującej.</span><span class="sxs-lookup"><span data-stu-id="b5166-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5166-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5166-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b5166-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5166-105">Remarks</span></span>  
 <span data-ttu-id="b5166-106">Operacja zakończy `StepOut` się po powrocie z bieżącej ramki do ramki wywołującej.</span><span class="sxs-lookup"><span data-stu-id="b5166-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="b5166-107">Jeśli `StepOut` jest wywoływana w kodzie niezarządzanym, krok zakończy się, gdy bieżąca ramka powróci do zarządzanego kodu, który go wywołał.</span><span class="sxs-lookup"><span data-stu-id="b5166-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="b5166-108">W .NET Framework w wersji 2,0 nie należy używać `StepOut` z ustawioną flagą STOP_UNMANAGED, ponieważ zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b5166-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="b5166-109">(Użyj [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) , aby ustawić flagi do wykonywania krokowo). Debugery międzyoperacyjności muszą przekroczyć kod natywny.</span><span class="sxs-lookup"><span data-stu-id="b5166-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5166-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5166-110">Requirements</span></span>  
 <span data-ttu-id="b5166-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5166-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5166-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b5166-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5166-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b5166-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5166-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5166-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
