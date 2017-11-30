---
title: "ICorDebugStepper::SetRangeIL — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetRangeIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df4c08b564f8789922ff49c075baca5e67b9208
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="29d0f-102">ICorDebugStepper::SetRangeIL — Metoda</span><span class="sxs-lookup"><span data-stu-id="29d0f-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="29d0f-103">Ustawia wartość określającą czy wywołań [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przekazać wartości, które są powiązane kodu natywnego lub względem Microsoft pośredniego kod języka (MSIL) metody, która jest trwa przeprowadził argumentu za pomocą.</span><span class="sxs-lookup"><span data-stu-id="29d0f-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29d0f-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29d0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29d0f-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="29d0f-106">[in] Ustaw `true` zakresy są względem kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="29d0f-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="29d0f-107">Ustaw `false` zakresy są względem kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="29d0f-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="29d0f-108">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="29d0f-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d0f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29d0f-109">Requirements</span></span>  
 <span data-ttu-id="29d0f-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29d0f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d0f-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29d0f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29d0f-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29d0f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29d0f-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
