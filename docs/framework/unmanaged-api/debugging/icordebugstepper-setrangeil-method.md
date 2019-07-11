---
title: ICorDebugStepper::SetRangeIL — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610225708bf990850fce73d6d7ff66c556e24e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760594"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="99c9c-102">ICorDebugStepper::SetRangeIL — Metoda</span><span class="sxs-lookup"><span data-stu-id="99c9c-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="99c9c-103">Ustawia wartość określającą, czy wywołania [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przekazać wartości, które są względem kodu natywnego lub względną Microsoft pośredniego kod language (MSIL) metody, która jest jest zmieniana argumentu za pomocą.</span><span class="sxs-lookup"><span data-stu-id="99c9c-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99c9c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99c9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99c9c-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="99c9c-106">[in] Ustaw `true` do określenia, że zakresy są względne wobec kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="99c9c-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="99c9c-107">Ustaw `false` do określenia, że zakresy są względne wobec kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="99c9c-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="99c9c-108">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="99c9c-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c9c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99c9c-109">Requirements</span></span>  
 <span data-ttu-id="99c9c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99c9c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c9c-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99c9c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99c9c-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99c9c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99c9c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
