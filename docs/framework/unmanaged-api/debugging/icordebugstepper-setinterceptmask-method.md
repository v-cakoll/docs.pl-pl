---
title: "ICorDebugStepper::SetInterceptMask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a99b504c0ce58ca6b89153667598cd4c2c682d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="557a6-102">ICorDebugStepper::SetInterceptMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="557a6-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="557a6-103">Ustawia wartość, która określa typy kodu, które zostaną wykorzystane do.</span><span class="sxs-lookup"><span data-stu-id="557a6-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="557a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="557a6-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="557a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="557a6-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="557a6-106">[in] Kombinacja wartości wyliczenia CorDebugIntercept, która określa typy kodu.</span><span class="sxs-lookup"><span data-stu-id="557a6-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="557a6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="557a6-107">Remarks</span></span>  
 <span data-ttu-id="557a6-108">Jeśli ustawiono bit interceptora, stepper ukończy po napotkaniu danego typu przechwytywaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="557a6-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="557a6-109">Jeśli bit jest wyczyszczone, intercepting kodu zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="557a6-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="557a6-110">`SetInterceptMask` Metoda może mieć nieprzewidziane interakcji z [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika).</span><span class="sxs-lookup"><span data-stu-id="557a6-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="557a6-111">Na przykład jeśli tylko widoczne (oznacza to,-wewnętrzny) część kod inicjujący klasa nie ma informacji o mapowaniu i STOP_NO_MAPPING_INFO nie została ustawiona (zobacz [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) — metoda i Cordebugunmappedstop — wyliczenie), stepper zostanie Przekrocz nad inicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="557a6-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="557a6-112">Domyślnie tylko INTERCEPT_NONE wartość `CorDebugIntercept` wyliczenie będą używane.</span><span class="sxs-lookup"><span data-stu-id="557a6-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="557a6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="557a6-113">Requirements</span></span>  
 <span data-ttu-id="557a6-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="557a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="557a6-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="557a6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="557a6-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="557a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="557a6-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="557a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
