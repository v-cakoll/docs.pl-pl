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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37b644227a6085352bed682f0ddd7c3455b54895
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760704"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="c1868-102">ICorDebugStepper::SetInterceptMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1868-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="c1868-103">Ustawia wartość, która określa typy kodu, które zostaną wykorzystane do.</span><span class="sxs-lookup"><span data-stu-id="c1868-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1868-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1868-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1868-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1868-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="c1868-106">[in] Kombinacja wartości wyliczenia cordebugintercept —, który określa typy kodu.</span><span class="sxs-lookup"><span data-stu-id="c1868-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1868-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1868-107">Remarks</span></span>  
 <span data-ttu-id="c1868-108">Jeśli ustawiono bit interceptor, stepper zostanie ukończone, gdy zostanie osiągnięty danego typu przechwytuje kodu.</span><span class="sxs-lookup"><span data-stu-id="c1868-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="c1868-109">Jeśli bit jest wyczyszczone, przechwytujący kod zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="c1868-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="c1868-110">`SetInterceptMask` Metoda może mieć nieprzewidziane interakcji z [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika).</span><span class="sxs-lookup"><span data-stu-id="c1868-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="c1868-111">Na przykład jeśli widoczne tylko dla (oznacza to, — wewnętrzny) część kodu inicjowania klasy brakuje informacji o mapowaniu i nie ustawiono STOP_NO_MAPPING_INFO (zobacz [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metody i Cordebugunmappedstop — wyliczenie), stepper przechodzi przez inicjowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="c1868-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="c1868-112">Domyślnie tylko INTERCEPT_NONE wartość `CorDebugIntercept` wyliczenie będą używane.</span><span class="sxs-lookup"><span data-stu-id="c1868-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1868-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1868-113">Requirements</span></span>  
 <span data-ttu-id="c1868-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1868-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1868-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1868-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1868-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1868-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1868-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1868-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
