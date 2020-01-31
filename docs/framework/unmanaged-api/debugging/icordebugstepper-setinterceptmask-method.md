---
title: ICorDebugStepper::SetInterceptMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 9792abb4ee38a45aae59eaf79f1f0499539bd2ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791769"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="ed482-102">ICorDebugStepper::SetInterceptMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed482-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="ed482-103">Ustawia wartość określającą typy kodu, do którego nastąpi.</span><span class="sxs-lookup"><span data-stu-id="ed482-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed482-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed482-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed482-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed482-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="ed482-106">podczas Kombinacja wartości wyliczenia CorDebugIntercept —, która określa typy kodu.</span><span class="sxs-lookup"><span data-stu-id="ed482-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed482-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed482-107">Remarks</span></span>  
 <span data-ttu-id="ed482-108">Jeśli ustawiono bit dla interceptora, stepper zakończy się po napotkaniu danego typu kodu przechwycenia.</span><span class="sxs-lookup"><span data-stu-id="ed482-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="ed482-109">Jeśli bit jest wyczyszczony, kod przechwycenia zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="ed482-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="ed482-110">Metoda `SetInterceptMask` może mieć nieprzewidziane interakcje z [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika).</span><span class="sxs-lookup"><span data-stu-id="ed482-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="ed482-111">Na przykład, jeśli jedyną widoczną częścią (czyli niewewnętrzną) fragmentu kodu inicjującego nie są informacje mapowania, a STOP_NO_MAPPING_INFO nie jest ustawiona (patrz metoda [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) i Wyliczenie CorDebugUnmappedStop —), stepper będzie przekroczyć inicjalizację klasy.</span><span class="sxs-lookup"><span data-stu-id="ed482-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="ed482-112">Domyślnie zostanie użyta tylko INTERCEPT_NONE wartość wyliczenia `CorDebugIntercept`.</span><span class="sxs-lookup"><span data-stu-id="ed482-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed482-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed482-113">Requirements</span></span>  
 <span data-ttu-id="ed482-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed482-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed482-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed482-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed482-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed482-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed482-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed482-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
