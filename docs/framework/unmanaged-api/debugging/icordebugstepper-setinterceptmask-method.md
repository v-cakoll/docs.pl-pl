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
ms.openlocfilehash: 7654a91180dd0b4148cfb85b35bf1ce730764f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422688"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="69ba2-102">ICorDebugStepper::SetInterceptMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="69ba2-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="69ba2-103">Ustawia wartość, która określa typy kodu, które zostaną wykorzystane do.</span><span class="sxs-lookup"><span data-stu-id="69ba2-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69ba2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69ba2-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69ba2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69ba2-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="69ba2-106">[in] Kombinacja wartości wyliczenia CorDebugIntercept, która określa typy kodu.</span><span class="sxs-lookup"><span data-stu-id="69ba2-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69ba2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69ba2-107">Remarks</span></span>  
 <span data-ttu-id="69ba2-108">Jeśli ustawiono bit interceptora, stepper ukończy po napotkaniu danego typu przechwytywaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="69ba2-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="69ba2-109">Jeśli bit jest wyczyszczone, intercepting kodu zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="69ba2-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="69ba2-110">`SetInterceptMask` Metoda może mieć nieprzewidziane interakcji z [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika).</span><span class="sxs-lookup"><span data-stu-id="69ba2-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="69ba2-111">Na przykład jeśli tylko widoczne (oznacza to,-wewnętrzny) część kod inicjujący klasa nie ma informacji o mapowaniu i STOP_NO_MAPPING_INFO nie została ustawiona (zobacz [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) — metoda i Cordebugunmappedstop — wyliczenie), stepper zostanie Przekrocz nad inicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="69ba2-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="69ba2-112">Domyślnie tylko INTERCEPT_NONE wartość `CorDebugIntercept` wyliczenie będą używane.</span><span class="sxs-lookup"><span data-stu-id="69ba2-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69ba2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69ba2-113">Requirements</span></span>  
 <span data-ttu-id="69ba2-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69ba2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69ba2-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69ba2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69ba2-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69ba2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69ba2-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69ba2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
