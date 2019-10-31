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
ms.openlocfilehash: 88270cb73515cc1a671bfb3fb5c479697ad7b359
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137542"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="66c35-102">ICorDebugStepper::SetRangeIL — Metoda</span><span class="sxs-lookup"><span data-stu-id="66c35-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="66c35-103">Ustawia wartość określającą, czy wywołania do [ICorDebugStepper:: StepRange —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przechodzą wartości argumentów, które są względne dla kodu natywnego lub względem kodu języka pośredniego firmy Microsoft (MSIL) metody, która jest testowana przez.</span><span class="sxs-lookup"><span data-stu-id="66c35-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66c35-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66c35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66c35-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="66c35-106">podczas Ustaw na `true`, aby określić, że zakresy są względne dla kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="66c35-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="66c35-107">Ustaw na `false`, aby określić, że zakresy są względne dla kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="66c35-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="66c35-108">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="66c35-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c35-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66c35-109">Requirements</span></span>  
 <span data-ttu-id="66c35-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c35-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c35-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66c35-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66c35-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66c35-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66c35-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c35-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
